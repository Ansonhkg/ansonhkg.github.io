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

- `yarn add jest`

- `yarn add babel-core@npm:@babel/core`
- `yarn add babel-jest`
- `yarn add babel-preset-env`
- `yarn add @babel/preset-env`

4. ##### And add the following to your package.json
```json
"babel": {
    "presets": [
      "@babel/preset-env"
    ]
  },
  "jest": {
    "transform": {
      "^.+.vue$": "vue-jest",
      "^.+.js$": "babel-jest"
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

### Useful links 
- [https://github.com/vuejs/vue-test-utils](https://github.com/vuejs/vue-test-utils)
- [https://github.com/alidcastano/nuxt-jest-puppeteer](https://github.com/alidcastano/nuxt-jest-puppeteer)
- [https://www.youtube.com/watch?v=vQ4A7EfAHOg](https://www.youtube.com/watch?v=vQ4A7EfAHOg)


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
