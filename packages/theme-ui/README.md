<p align="center">
  <img
    src="/packages/docs/static/logo.png"
    width="96"
    height="96"
  />
</p>

<h1 align="center">Theme UI</h1>

<p align="center">
  <strong>The Design Graph Framework</strong>
</p>

&nbsp;

<p align="center">
  <a href="https://github.com/system-ui/theme-ui">
    <img src="https://badgen.net/badge/-/github?icon=github&label" alt="GitHub" />
  </a>
  <a href="https://github.com/system-ui/theme-ui/stargazers">
    <img src="https://badgen.net/github/stars/system-ui/theme-ui" alt="GitHub Stars"/>
  </a>
  <a>
    <img alt="npm (latest)" src="https://img.shields.io/npm/v/theme-ui/latest"/>
  </a>
  <a>
    <img alt="npm (next)" src="https://img.shields.io/npm/v/theme-ui/next?color=%23e044aa"/>
  </a>
  <br />
  <a href="https://github.com/system-ui/theme-ui/actions?query=workflow%3ACI">
    <img src="https://github.com/system-ui/theme-ui/workflows/CI/badge.svg" alt="Build Status"/>
  </a>
  <a href="https://github.com/system-ui/theme-ui/graphs/contributors">
    <img src="https://img.shields.io/github/contributors/system-ui/theme-ui" alt="Contributors" />
  </a>
  <a href="https://github.com/badges/shields/pulse" >
    <img src="https://img.shields.io/github/commit-activity/m/system-ui/theme-ui" alt="Activity" />        
  </a>
  <br />
  <a href="https://badgen.net/bundlephobia/minzip/theme-ui">
    <img
      src="https://badgen.net/bundlephobia/minzip/theme-ui"
      alt="Size"
    />
  </a>
  <a href="https://bundlephobia.com/result?p=theme-ui">
    <img
      src="https://badgen.net/bundlephobia/tree-shaking/theme-ui"
      alt="Tree Shaking"
    />
  </a>
  <a href="https://github.com/system-ui/theme-ui/blob/stable/LICENSE.md">
    <img
      src="https://badgen.net/badge/license/MIT/blue"
      alt="MIT license"
    />
  </a>
  <a href="https://discord.gg/stp6BY7MXA">
    <img src="https://img.shields.io/discord/778553042466635786?color=%237289da&logo=discord" alt="Join our Discord community"/>
  </a>
</p>

\
Theme UI is a library for creating themeable user interfaces based on constraint-based design principles. Build custom component libraries, design systems, web applications, Gatsby themes, and more with a flexible API for best-in-class developer ergonomics.

**[stable] docs**: https://theme-ui.com \
**[develop] (v0.6.0-alpha) docs**: https://dev.theme-ui.com

[stable]: https://github.com/system-ui/theme-ui/tree/stable
[develop]: https://github.com/system-ui/theme-ui/tree/develop

---

Built for design systems, white-labels, themes, and other applications where customizing colors, typography, and layout are treated as first-class citizens
and based on a standard [Theme Specification][],
Theme UI is intended to work in a variety of applications, libraries, and other UI components.
Colors, typography, and layout styles derived from customizable theme-based design scales
help you build UI rooted in constraint-based design principles.

- The next evolution of Styled System
- From the creators of utility-based, atomic CSS methodologies
- Theme-based styling with the `sx` prop
- Style [MDX][] content with a simple, expressive API
- Works with [Typography.js][] themes
- Compatible with virtually any UI component library
- Works with existing [Styled System][] components
- Quick mobile-first responsive styles
- Built-in support for dark modes
- Primitive page layout components
- Plugin for use in [Gatsby][] sites and themes
- Completely customizable with robust theming
- Built with a standard [Theme Specification][] for interoperability
- Built with [Emotion][] for scoped styles

[emotion]: https://emotion.sh
[mdx]: https://mdxjs.com
[styled system]: https://styled-system.com
[gatsby]: https://gatsbyjs.org
[theme specification]: https://system-ui.com/theme
[typography.js]: https://github.com/KyleAMathews/typography.js

## Getting Started

```sh
npm install theme-ui
```

Any styles in your app can reference values from the global `theme` object.
To provide the theme in context,
wrap your application with the `ThemeProvider` component and pass in a custom `theme` object.

```jsx
// basic usage
import { ThemeProvider } from 'theme-ui'
import theme from './theme'

export default (props) => (
  <ThemeProvider theme={theme}>{props.children}</ThemeProvider>
)
```

The `theme` object follows the System UI [Theme Specification](https://theme-ui.com/theme-spec/),
which lets you define custom color palettes, typographic scales, fonts, and more.
Read more about [theming](https://theme-ui.com/theming).

```js
// example theme.js
export default {
  fonts: {
    body:
      'system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", sans-serif',
    heading: '"Avenir Next", sans-serif',
    monospace: 'Menlo, monospace',
  },
  colors: {
    text: '#000',
    background: '#fff',
    primary: '#33e',
  },
}
```

## `sx` prop

The `sx` prop works similarly to Emotion's `css` prop, accepting style objects to add CSS directly to an element in JSX, but includes extra theme-aware functionality.
Using the `sx` prop for styles means that certain properties can reference values defined in your `theme` object.
This is intended to make keeping styles consistent throughout your app the easy thing to do.

The `sx` prop only works in modules that have defined a custom pragma at the top of the file, which replaces the default React JSX functions.
This means you can control which modules in your application opt into this feature without the need for a Babel plugin or additional configuration.

```jsx
/** @jsxImportSource theme-ui */

export default (props) => (
  <div
    sx={{
      fontWeight: 'bold',
      fontSize: 4, // picks up value from `theme.fontSizes[4]`
      color: 'primary', // picks up value from `theme.colors.primary`
    }}>
    Hello
  </div>
)
```

Read more about [how the custom pragma works](https://theme-ui.com/guides/how-it-works/#jsx-pragma).

## Responsive styles

The `sx` prop also supports using arrays as values to change properties responsively with a mobile-first approach.
This API originated in [Styled System][] and is intended as [a terser syntax for applying responsive styles](https://styled-system.com/guides/array-props) across a singular dimension.

```jsx
/** @jsxImportSource theme-ui */

export default (props) => (
  <div
    sx={{
      // applies width 100% to all viewport widths,
      // width 50% above the first breakpoint,
      // and 25% above the next breakpoint
      width: ['100%', '50%', '25%'],
    }}
  />
)
```

---

## Documentation

- [Theming](https://theme-ui.com/theming)
- [The `sx` Prop](https://theme-ui.com/sx-prop)
- [Layout](https://theme-ui.com/layout)
- [Color Modes](https://theme-ui.com/color-modes)
- [Themed](https://theme-ui.com/themed)
- [MDX Components](https://theme-ui.com/mdx-components)
- [Theme Spec](https://theme-ui.com/theme-spec)
- [Gatsby Plugin](https://theme-ui.com/packages/gatsby-plugin)
- [API](https://theme-ui.com/api)

MIT License
