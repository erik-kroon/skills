# SolidJS Rule Examples

Load this file when a Solid best-practice task needs concrete transformations.
Adapt names, imports, route conventions, and SolidStart version to the project.

## Contents

- [`reactive-keep-props-live`](#reactive-keep-props-live)
- [`reactive-no-effect-derived-state`](#reactive-no-effect-derived-state)
- [`async-resource-source`](#async-resource-source)
- [`async-no-fetch-in-effect`](#async-no-fetch-in-effect)
- [`async-query-cache` and `async-revalidate-targeted`](#async-query-cache-and-async-revalidate-targeted)
- [`async-suspense-boundaries`](#async-suspense-boundaries)
- [`render-for-vs-index`](#render-for-vs-index)
- [`effect-cleanup-subscriptions`](#effect-cleanup-subscriptions)
- [`effect-delegated-vs-native-events`](#effect-delegated-vs-native-events)
- [`server-request-scoped-state`](#server-request-scoped-state)
- [`server-no-browser-apis`](#server-no-browser-apis)
- [`bundle-lazy-heavy-components`](#bundle-lazy-heavy-components)
- [`advanced-run-with-owner`](#advanced-run-with-owner)

## `reactive-keep-props-live`

Props are reactive proxies. Destructuring or assigning a prop to a plain value
takes a snapshot.

Bad:

```tsx
function Greeting(props: { name: string }) {
  const { name } = props;
  return <p>Hello {name}</p>;
}
```

Good:

```tsx
function Greeting(props: { name: string }) {
  return <p>Hello {props.name}</p>;
}
```

Good when a local name is useful:

```tsx
function Greeting(props: { name: string }) {
  const name = () => props.name;
  return <p>Hello {name()}</p>;
}
```

Good when splitting pass-through props:

```tsx
import { splitProps } from "solid-js";

function Field(props: { label: string; name: string; disabled?: boolean }) {
  const [local, input] = splitProps(props, ["label"]);
  return (
    <label>
      {local.label}
      <input {...input} />
    </label>
  );
}
```

## `reactive-no-effect-derived-state`

Do not use an effect to synchronize state that can be derived from current
reactive inputs.

Bad:

```tsx
const [firstName, setFirstName] = createSignal("Ada");
const [lastName, setLastName] = createSignal("Lovelace");
const [fullName, setFullName] = createSignal("");

createEffect(() => {
  setFullName(`${firstName()} ${lastName()}`);
});
```

Good:

```tsx
const [firstName, setFirstName] = createSignal("Ada");
const [lastName, setLastName] = createSignal("Lovelace");
const fullName = () => `${firstName()} ${lastName()}`;
```

Good for expensive or shared derived values:

```tsx
const filteredRows = createMemo(() => {
  const q = search().trim().toLowerCase();
  return rows().filter((row) => row.name.toLowerCase().includes(q));
});
```

## `async-resource-source`

Drive async resources from the narrowest source that should trigger refetching.
Return `false`, `null`, or `undefined` when the fetcher should not run.

Bad:

```tsx
const [user] = createResource(async () => {
  if (!props.userId || !props.enabled) return undefined;
  return fetchUser(props.userId);
});
```

Good:

```tsx
const userSource = () => (props.enabled && props.userId ? props.userId : false);
const [user] = createResource(userSource, fetchUser);
```

## `async-no-fetch-in-effect`

Use resources, router data APIs, or actions for application data. Keep effects
for side effects and integrations.

Bad:

```tsx
const [profile, setProfile] = createSignal<Profile>();

createEffect(async () => {
  const res = await fetch(`/api/users/${props.userId}`);
  setProfile(await res.json());
});
```

Good:

```tsx
const [profile] = createResource(() => props.userId, async (userId) => {
  const res = await fetch(`/api/users/${encodeURIComponent(userId)}`);
  if (!res.ok) throw new Error("Failed to load profile");
  return (await res.json()) as Profile;
});
```

Good with Solid Router:

```tsx
import { createAsync, query } from "@solidjs/router";

const getProfile = query(async (userId: string) => {
  const res = await fetch(`/api/users/${encodeURIComponent(userId)}`);
  if (!res.ok) throw new Error("Failed to load profile");
  return (await res.json()) as Profile;
}, "profile");

function ProfileView(props: { userId: string }) {
  const profile = createAsync(() => getProfile(props.userId));
  return <h1>{profile()?.name}</h1>;
}
```

## `async-query-cache` and `async-revalidate-targeted`

Use `query()` for repeatable route reads. In SolidStart, preloaded queries can
be revalidated automatically by server actions as a single-flight mutation. Use
manual `revalidate()` for refresh controls or mutation flows that need explicit
targeting.

```tsx
import {
  action,
  createAsync,
  query,
  revalidate,
  type RouteDefinition,
  type RouteSectionProps,
} from "@solidjs/router";

const getProduct = query(async (id: string) => {
  "use server";
  return db.products.get(id);
}, "product");

const updateProduct = action(async (id: string, formData: FormData) => {
  "use server";
  await db.products.update(id, {
    name: String(formData.get("name") ?? ""),
  });
}, "updateProduct");

export const route = {
  preload: ({ params }) => getProduct(params.id),
} satisfies RouteDefinition;

export default function Product(props: RouteSectionProps) {
  const product = createAsync(() => getProduct(props.params.id));

  return (
    <>
      <p>{product()?.name}</p>
      <form action={updateProduct.with(props.params.id)} method="post">
        <input name="name" />
        <button>Save</button>
      </form>
      <button onClick={() => void revalidate(getProduct.keyFor(props.params.id))}>
        Refresh
      </button>
    </>
  );
}
```

## `async-suspense-boundaries`

Put Suspense around the subtree that reads suspense-tracked async data. Keep the
stable shell outside the boundary when it can render immediately.

Bad:

```tsx
function Page() {
  const profile = createAsync(() => getProfile());
  return <main>{profile()?.name}</main>;
}
```

Good:

```tsx
function Page() {
  return (
    <main>
      <Header />
      <Suspense fallback={<ProfileSkeleton />}>
        <ProfilePanel />
      </Suspense>
    </main>
  );
}

function ProfilePanel() {
  const profile = createAsync(() => getProfile());
  return <h1>{profile()?.name}</h1>;
}
```

## `render-for-vs-index`

Use `<For>` when item identity matters or rows reorder. Use `<Index>` when
positions are stable and values at those positions update.

Good for identity lists:

```tsx
<For each={users()} fallback={<p>No users</p>}>
  {(user) => <UserRow user={user} />}
</For>
```

Good for stable-index primitive values:

```tsx
<Index each={scores()}>
  {(score, index) => (
    <li>
      #{index + 1}: {score()}
    </li>
  )}
</Index>
```

Avoid dynamic `array.map()` in reactive JSX:

```tsx
// Bad for dynamic lists
<ul>{users().map((user) => <UserRow user={user} />)}</ul>
```

## `effect-cleanup-subscriptions`

Register external subscriptions, timers, observers, and event listeners under
the current owner with `onCleanup`.

Bad:

```tsx
function Tracker() {
  setInterval(() => sendHeartbeat(), 10000);
  return null;
}
```

Good:

```tsx
import { onCleanup } from "solid-js";

function Tracker() {
  const id = window.setInterval(() => sendHeartbeat(), 10000);
  onCleanup(() => window.clearInterval(id));
  return null;
}
```

## `effect-delegated-vs-native-events`

Solid delegates common events like `click` and `input`. Use native `on:*`
events when propagation behavior, custom events, or occasional high-volume
events make delegation a poor fit.

Delegated:

```tsx
<button onClick={save}>Save</button>
```

Native:

```tsx
<button
  on:click={(event) => {
    event.stopPropagation();
    save();
  }}
>
  Save
</button>
```

## `server-request-scoped-state`

Do not store request-specific data in module-level variables. It can leak across
SSR requests.

Bad:

```ts
let currentUserId: string | undefined;

export async function loadUser() {
  "use server";
  currentUserId = await readUserIdFromSession();
  return db.users.get(currentUserId);
}
```

Good:

```ts
export async function loadUser() {
  "use server";
  const userId = await readUserIdFromSession();
  return db.users.get(userId);
}
```

## `server-no-browser-apis`

Keep browser APIs out of server-rendered execution paths.

Bad:

```tsx
const theme = localStorage.getItem("theme");
```

Good:

```tsx
import { createSignal, onMount } from "solid-js";

const [theme, setTheme] = createSignal("system");

onMount(() => {
  setTheme(localStorage.getItem("theme") ?? "system");
});
```

Use a client-only boundary or dynamic import for browser-only libraries that
touch `window` at module evaluation time.

## `bundle-lazy-heavy-components`

Split rare or heavy UI, then preload on strong intent.

```tsx
import { createSignal, lazy, Show, Suspense } from "solid-js";

const ChartEditor = lazy(() => import("./ChartEditor"));

function Dashboard() {
  const [editing, setEditing] = createSignal(false);

  return (
    <>
      <button
        onMouseEnter={() => ChartEditor.preload()}
        onFocus={() => ChartEditor.preload()}
        onClick={() => setEditing(true)}
      >
        Edit chart
      </button>
      <Show when={editing()}>
        <Suspense fallback={<EditorSkeleton />}>
          <ChartEditor />
        </Suspense>
      </Show>
    </>
  );
}
```

## `advanced-run-with-owner`

Use `runWithOwner` only when a callback must create Solid computations later.
It restores owner synchronously, but code after `await` runs without that owner
or dependency tracking.

```tsx
import { createEffect, getOwner, runWithOwner } from "solid-js";

function Bridge() {
  const owner = getOwner();

  subscribe((value) => {
    if (!owner) return;
    runWithOwner(owner, () => {
      createEffect(() => {
        console.log("value", value);
      });
    });
  });

  return null;
}
```

Prefer creating the computation inside the component when possible. Use owner
bridging only for integration callbacks that cannot be structured normally.
