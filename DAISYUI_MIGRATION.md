# DaisyUI Migration Plan

## Goal
Replace Tailwind utility classes with DaisyUI semantic classes throughout live_table.

## Benefits
1. **Simpler code**: `table-pin-rows` instead of custom sticky CSS
2. **Better theming**: DaisyUI handles dark mode automatically
3. **Semantic classes**: `card`, `badge`, `btn` instead of utility combinations
4. **Fixed headers**: Built-in with `table-pin-rows` (solves issue #19)
5. **Less custom CSS**: DaisyUI components work out of the box

## Key Changes

### Table Classes
**Before (Tailwind):**
```html
<table class="table divide-y dark:divide-gray-700">
  <thead class="bg-gray-50 dark:bg-gray-800">
```

**After (DaisyUI):**
```html
<table class="table table-zebra table-pin-rows">
  <thead>
```

### Container Classes
**Before (Tailwind):**
```html
<div class="overflow-hidden shadow sm:rounded-lg">
```

**After (DaisyUI):**
```html
<div class="card bg-base-100 shadow-xl">
```

### Button Classes
**Before (Tailwind):**
```html
<button class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500">
```

**After (DaisyUI):**
```html
<button class="btn btn-primary">
```

## New Options

### `pin_header` Option
Add to table_options:
```elixir
table_options: %{
  pin_header: true,  # default: true
  zebra: true,       # default: false
  size: :md          # :xs, :sm, :md, :lg
}
```

## Implementation Steps

1. ✅ Document migration plan
2. ⬜ Update table_component.ex with DaisyUI classes
3. ⬜ Add pin_header, zebra, size options
4. ⬜ Update examples in docs/
5. ⬜ Update README.md
6. ⬜ Update usage_rules.md
7. ⬜ Test in Sanjuan project
8. ⬜ Consider PR to upstream

## Testing Checklist

- [ ] Fixed header works with table-pin-rows
- [ ] Zebra striping works
- [ ] Dark mode theming
- [ ] Responsive behavior
- [ ] Empty states
- [ ] Actions column
- [ ] Card mode (if applicable)
- [ ] All table sizes (xs, sm, md, lg)

