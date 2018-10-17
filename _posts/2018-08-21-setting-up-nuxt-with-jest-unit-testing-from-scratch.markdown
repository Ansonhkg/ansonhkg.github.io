---
layout: post
title:  Setting up Nuxt with Jest Unit Testing from Scratch
date:   2018-08-21 22:42:00 +0100
categories: Web-Development
author: Anson Cheung
---

# Setting up Nuxt with Jest Unit Testing from Scratch
![](https://image.ibb.co/cW8uTK/image.png)

1. ##### Install Nuxt.js starter template or install it with vue-cli
`vue init nuxt-community/starter-template nuxt-jest`

2. ##### Enter the directory and install dependencies
`cd nuxt-jest`
`yarn add jest`

3. ##### Jest would try to run vue component inside JavaScript, but the component isn't a valid JavaScript. So when Jest runs it, it will encounter the "<" token syntax error. We need to transform our component before Jest runs it. To do that, we will need to install:
- `yarn add vue-jest`
-  `yarn add babel-jest`

4. ##### And add the following to your package.json
```json
"babel": {
  "presets": [
    "env"
  ]
},
```
```json
"jest": {
  "transform": {
    "^.+\\.js$": "babel-jest",
    "^.+\\.vue$": "vue-jest"
  }
}
```

5. ##### Finally, let's install vue/test-utils. It's a unit testing utility library that makes testing easier. The main method that it exports is the { mount } method, which takes a component and mounts it, and returns a wrapper than contains the mounter component instance as well as helper methods to assert and render against the component render tree.

- `yarn add @vue/test-utils`

> **Counter.vue**

```javascript
<template>
    <div>
        <div>Counter: {{ counter }}</div>
        <button @click="counter++">Increment</button>
    </div>
</template>

<script>
export default {
    data(){
        return{
            counter: 0
        }
    }
}
</script>
```



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

### Useful links 
- https://github.com/vuejs/vue-test-utils
- https://github.com/alidcastano/nuxt-jest-puppeteer
- https://www.youtube.com/watch?v=vQ4A7EfAHOg

> **Counter.spec.js**

```javascript
import { mount } from '@vue/test-utils'
import Counter from './Counter.vue'

describe('Counter.vue', () => {
    test('Setup correctly', () => {
        expect(true).toBe(true)
    })
    test('increments the counter value when button is clicked', () => {
        const wrapper = mount(Counter)
        expect(wrapper.text()).toContain('Counter: 0')
        
    })
})
```


<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = window.location.href;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = 'setting-up-nuxt-with-jest-unit-testing-from-scratch'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://ansonc.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
```
