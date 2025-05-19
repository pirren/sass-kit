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

## Customization
Customizing any way you see fit. Recommended starting points are variables and utility classes.

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

Modify `utilities/_utilities.scss` to change which utility classes and generated and how. For example:
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
Responsive: true indicates it will output responsive variants. The list of variants will looks like this:
```
.p-0 { ... }
.p-1 { ... }
.p-2 { ... }
...
.md:p-0 { ... } // Kicks in at media breakpoint medium, defined in _variables.scss
.md:p-1 { ... } // Kicks in at media breakpoint medium, defined in _variables.scss
.md:p-2 { ... } // Kicks in at media breakpoint medium, defined in _variables.scss
...
```

Utility classes will always take precedent over others (`!important`) with the cascading order of responsive variations taking highest priority.