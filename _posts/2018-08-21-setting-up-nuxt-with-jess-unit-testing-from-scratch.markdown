# Setting up Nuxt with Jest Unit Testing from Scrach
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
- https://github.com/vuejs/vue-test-utils
- https://github.com/alidcastano/nuxt-jest-puppeteer
- https://www.youtube.com/watch?v=vQ4A7EfAHOg
