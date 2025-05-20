# sass-kit

A modular, scalable and utility-first Sass framework designed for consistent, easy and maintainable UI development. It includes design tokens, mixins, functions and responsive utility class generation. 

Influenced by both bootstrap and tailwind in some regards.

Designed and tested for development using Vue3 + Vite.

---

## Installation

First install `sass` and `sass-loader`:

`npm install -D sass sass-loader`

---

## Setup

Import main Sass file into project, usually main.js or equivalent:
`import './assets/styles/main.scss'`

Make sure your `main.scss` file includes **at least** the necessary modules:
```
@use 'base/reset';
@use 'base/typography';
@use 'utilities/utilities';
...
```

---

## Customization
Customize any way you see fit. Recommended starting points are variables and utility classes.

### Adjust variables

Customize by tweaking variables in  `abstracts/_variables.scss`:
```
// Change the color palette
// Set the primary color
$color-primary: #004d40;

...

// Update typography
$default-font-size: 1rem;
$font-heading: 'Nunito', sans-serif;
$font-body: 'Work Sans', sans-serif;
```

### Customize utilities

Modify `utilities/_utilities.scss` to change which utility classes are generated and how. For example:
  - Add new utility classes
  - Adjust spacing scale or breakpoints
  - Customize resulting class names

A class block looks like this:
```
  "padding": (
    responsive: true,
    property: padding,
    class: p,
    values: $spacers
  ),
```
`responsive: true` indicates it will output responsive variants. A responsive class will output like this:
```
.p-0 { ... }
.p-1 { ... }
.p-2 { ... }

...

.md:p-0 { ... } // Kicks in at media breakpoint medium(md), defined in _variables.scss
.md:p-1 { ... } // Kicks in at media breakpoint medium(md), defined in _variables.scss

...

.lg:p-0 { ... } // Kicks in at media breakpoint large(lg), defined in _variables.scss
.lg:p-1 { ... } // Kicks in at media breakpoint large(lg), defined in _variables.scss

...
```

Utility classes will all take precedence with important flag (`!important`), with the cascading order of responsive variations taking highest priority.

---

## Cheat sheet

### Install Sass for local testing

```
npm init -y
npm install sass --save-dev
```

package.json: 

```
...
  "scripts": {
    "sass": "sass --watch main.scss:dist/main.css --style=compressed"
  }
...
```

Finally run with `npm run sass`