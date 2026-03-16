# Changelog - versions

## 0.3.2

- Added nullish coalescing (`??`) and optional chaining (`?.`, `?.[`, `?.()`) to the expression evaluator
- Fixed falsy values in `x-data-*` / `x-attr`: `0`, `false`, and `""` now correctly set attributes instead of removing them (only `undefined` and `null` remove)
- Fixed event handler `this` context: handlers now receive the real component instance, enabling private fields (`#path`, etc.) in methods
- Event handlers: `@click="openRoot"` now auto-invokes when the expression evaluates to a function (Alpine-style), in addition to `@click="openRoot()"`

## 0.3.1

- Fixed double-processing of plugin attributes: `x-text.*` (dotted) attributes are now skipped by the generic `x-attr` loop, preventing spurious warnings and duplicate evaluation
- Added `x-text` to the generic attribute exclusion list (already handled by its own dedicated processing section)
- Build: plugin `.md` documentation files are now copied to `dist/` preserving folder structure

## 0.3.0

- 'render' replaced by 'x-text' for coherence
- `@event=` get alias `x-on:event-name=` for API coherence
- logs="events" is now implemented for events logs
- html syntax helper function is now included and importable

## 0.2.3

- Fixed x-for context propagation: reused nodes with x-key now update context on all descendants, not just the root node
- Fixed x-for DOM reordering: iterate backwards to ensure correct node positioning when items are moved

## 0.2.2

- fixed nested x-for handling

## 0.2.1

- x-key diffing algorithm is now reusing DOM nodes thus greatly optimzing rendering (up to 50% faster!)

## 0.2.0

- remove plugins, focusing on core library
- state and rendering target element are completely decoupled. The function requires both state and target now : rebindx(state, element)

## 0.1.4

- Mini Evaluator is now directly embeded in `rebindx`

## 0.1.3

- Added conditional logging system for plugins and core features
- Removed x-click-outside plugin
- Fixed plugin attribute handling and re-rendering
- Improved plugin logging control via `logs` attribute

## 0.1.1

- Inlined plugin core into `rebindx.js`, removing dependence on external rebind-core.js.
- Added chainable plugin API: `.use()`, `.process()`, `plugins`, and `parsePluginCall` directly on `rebindx`.
- Fixed plugin attribute lookup to avoid invalid CSS selector issues for `render.plugin`.

## 0.1.0

- Hidden elements (`x-if`) now reside in an in-memory `DocumentFragment` instead of a `<template>`, preventing hidden nodes from cluttering the DOM or shadow DOM.
- `<template x-for>` loops are now tracked from both the live DOM and the hidden fragment for correct re-rendering.
