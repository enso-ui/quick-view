# Quick View
[![License](https://img.shields.io/badge/license-MIT-10b981.svg)](https://github.com/enso-ui/quick-view/blob/master/LICENSE)
[![Stable](https://img.shields.io/badge/stable-3.2.8-2563eb.svg)](https://www.npmjs.com/package/@enso-ui/quick-view)
[![Downloads](https://img.shields.io/npm/dm/@enso-ui/quick-view.svg)](https://www.npmjs.com/package/@enso-ui/quick-view)
[![Vue](https://img.shields.io/badge/vue-3.x-42b883.svg)](https://vuejs.org/)
[![JavaScript](https://img.shields.io/badge/javascript-ES2020-f7df1e.svg)](https://developer.mozilla.org/docs/Web/JavaScript)
[![SCSS](https://img.shields.io/badge/scss-supported-c6538c.svg)](https://sass-lang.com/)
[![npm](https://img.shields.io/badge/npm-package-cb3837.svg)](https://www.npmjs.com/package/@enso-ui/quick-view)
[![Issues](https://img.shields.io/github/issues/enso-ui/quick-view.svg)](https://github.com/enso-ui/quick-view/issues)
[![Merge Requests](https://img.shields.io/github/issues-pr/enso-ui/quick-view.svg)](https://github.com/enso-ui/quick-view/pulls)
## Description
Slide-out quick-view panel for Enso UI.
## Installation
Install the package:

```bash
yarn add @enso-ui/quick-view
```
## Features
- exports `QuickView` as its public surface
- renders the panel through `Teleport` directly under `body`, avoiding parent stacking contexts and overflow clipping
- keeps the slide transition active while using a teleported panel
- supports Bulma column responsiveness through classes passed on the component
- aligns responsive panels to the right edge by default
- closes when the delete control is clicked
- closes when the user presses `Escape`
## Usage
```vue
<script setup>
import QuickView from '@enso-ui/quick-view/bulma';
</script>

<template>
    <quick-view class="is-one-third-desktop is-half-tablet is-full-mobile"
        @close="quickView = false"
        v-if="quickView">
        ...
    </quick-view>
</template>
```
## API
### `QuickView`

Public export available from `@enso-ui/quick-view/bulma`.

Attributes:
- classes passed to `QuickView` are applied to the internal Bulma `.column`, so standard column sizing helpers can control panel width responsively
- non-class attributes are not applied to the wrapper panel

Events:
- `close` is emitted after the panel is closed by the delete control, by `Escape`, or after the leave transition completes
## Depends On
- `@enso-ui/transitions`
- `@enso-ui/ui`
- `bulma`
- `pinia`
## Contributions
are welcome. Pull requests are great, but issues are good too.
Thank you to all the people who already contributed to Enso!
## License
[MIT](https://github.com/enso-ui/quick-view/blob/master/LICENSE)
