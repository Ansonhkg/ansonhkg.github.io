---
layout: post
title:  Setting up Nuxt with Tailwind CSS
date:   2018-08-21 22:50:00 +0100
categories: Web-Development
author: Anson Cheung
---

# Setting up Nuxt with Tailwind CSS
![](https://camo.githubusercontent.com/4aa5532ee9baf623c95b901372002dfa4e97ff01/687474703a2f2f696d6775722e636f6d2f56344c746f49492e706e67) ![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTU37MsS36DmMgNmpJJVzZkRgetfpBNTwG5VkvQkB8GATlV6QY7dw)

##### Adding NPM packages
`yarn add tailwindcss`

##### Create tailwind configuration file
`./node_modules/.bin/tailwind init tailwind.config`

##### Create a CSS file (~/assets/css/tailwind.css) with the following content

```
/**
 * This injects Tailwind's base styles, which is a combination of
 * Normalize.css and some additional base styles.
 *
 * You can see the styles here:
 * https://github.com/tailwindcss/tailwindcss/blob/master/css/preflight.css
 *
 * If using `postcss-import`, you should import this line from it's own file:
 *
 * @import "./tailwind-preflight.css";
 *
 * See: https://github.com/tailwindcss/tailwindcss/issues/53#issuecomment-341413622
 */
 @tailwind preflight;

 /**
  * Here you would add any of your custom component classes; stuff that you'd
  * want loaded *before* the utilities so that the utilities could still
  * override them.
  *
  * Example:
  *
  * .btn { ... }
  * .form-input { ... }
  *
  * Or if using a preprocessor or `postcss-import`:
  *
  * @import "components/buttons";
  * @import "components/forms";
  */

 /**
  * This injects all of Tailwind's utility classes, generated based on your
  * config file.
  *
  * If using `postcss-import`, you should import this line from it's own file:
  *
  * @import "./tailwind-utilities.css";
  *
  * See: https://github.com/tailwindcss/tailwindcss/issues/53#issuecomment-341413622
  */
 @tailwind utilities;

 /**
  * Here you would add any custom utilities you need that don't come out of the
  * box with Tailwind.
  *
  * Example :
  *
  * .bg-pattern-graph-paper { ... }
  * .skew-45 { ... }
  *
  * Or if using a preprocessor or `postcss-import`:
  *
  * @import "utilities/background-patterns";
  * @import "utilities/skew-transforms";
  */
```

- `yarn add vue-jest`

-  `yarn add babel-jest`

##### Create a postcss.config.js in your project root with the following content

```javascript
module.exports = {
  plugins: [
    require('tailwindcss')('./tailwind.js'),
    require('autoprefixer')
  ]
}
```

##### Add postcss in build before extend

```javascript
postcss: [
     require('tailwindcss')('./tailwind.js'),
     require('autoprefixer')
   ],
```

##### Add CSS after build in nuxt.config.js

```javascript
css: ['~/assets/css/tailwind.css']
```
