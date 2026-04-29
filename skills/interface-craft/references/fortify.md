# Fortify Mode

Use fortify mode to make an interface robust in real conditions.

## Check

- Long names, long words, translated strings, and narrow containers.
- Empty data, partial data, stale data, and permission-denied data.
- Loading, optimistic, pending, retry, timeout, and offline states.
- Error states that preserve user input and provide recovery.
- Disabled states that explain why the action is unavailable.
- Dates, numbers, currencies, units, and time zones.
- Input validation and sanitization where UI accepts user content.
- Focus management after async changes, modal close, route changes, and errors.
- Layout stability with images, media, dynamic content, and virtualized lists.
- Performance under large lists, slow devices, and slow networks.

## Stress Cases

Use concrete test data: longest plausible customer name, missing avatar,
permission denied, empty list, failed save, slow request, translated label,
keyboard-only interaction, and reduced motion.

## Output

- `Edge cases covered`
- `State gaps fixed`
- `Locale/text issues`
- `Verification`
- `Remaining fortification risks`
