---
layout: post
title:  Publish Vue component as NPM Package in 5 minutes.
date:   2019-10-12 13:53:00 +0100
categories: Web-Development Vue Javascript
author: Anson Cheung
---

# Publish Vue component as NPM Package in 5 minutes.

- [Publish Vue component as NPM Package in 5 minutes.](#publish-vue-component-as-npm-package-in-5-minutes)
- [Expected Usage](#expected-usage)
- [Steps](#steps)
  - [Folder strcture](#folder-strcture)
  - [package.json](#packagejson)
  - [./src/index.js](#srcindexjs)
  - [./build/rollup.config.js](#buildrollupconfigjs)
  - [./src/my-component.vue](#srcmy-componentvue)
- [Serve](#serve)
- [Build](#build)
- [Publish](#publish)

# Expected Usage

In your Vue app 
```html
<template>
    <MyComponent></MyComponent>
</template>

<script>
import MyComponent from '@ansonhkg/my-component'
default export {
    components:{
        MyComponent
    }
}
</script>
```

---

# Steps

## Folder strcture

Generate the following directory structure in your project folder.

```
package.json
build/
    rollup.config.js
src/
    index.js
    my-component.vue
dist/
```

## package.json

- Minimum setup for package.json. Replace `my-component` with your component name. 
- `"name": "my-component"` is referring to your npm package name that you are going to publish. It has to be unique, so normally I would prepend it with my username eg. `"name": "@ansonhkg/my-component"`.

```JSON
{
  "name": "@ansonhkg/my-component", // <== CHANGE THIS
  "version": "0.0.1",
  "main": "dist/my-component.umd.js", // <== CHANGE THIS
  "module": "dist/my-component.esm.js", // <== CHANGE THIS
  "unpkg": "dist/my-component.min.js", // <== CHANGE THIS
  "browser": {
    "./sfc": "src/my-component.vue" // <== CHANGE THIS
  },
  "scripts": {
    "build": "npm run build:umd & npm run build:es & npm run build:unpkg",
    "build:umd": "rollup --config build/rollup.config.js --format umd --file dist/my-component.umd.js", // <== CHANGE THIS
    "build:es": "rollup --config build/rollup.config.js --format es --file dist/my-component.esm.js", // <== CHANGE THIS
    "build:unpkg": "rollup --config build/rollup.config.js --format iife --file dist/my-component.min.js" // <== CHANGE THIS
  },
  "devDependencies": {
    "rollup": "^1.17.0",
    "rollup-plugin-buble": "^0.19.8",
    "rollup-plugin-commonjs": "^10.0.1",
    "rollup-plugin-vue": "^5.0.1",
    "vue": "^2.6.10",
    "vue-template-compiler": "^2.6.10"
  }
}
```

## ./src/index.js

This file provides an `install` function for Vue to detect if this indeed a Vue application, then install the component automatically.

```js
// Import vue component
import component from './my-component.vue'; // <== CHANGE THIS

// Declare install function executed by Vue.use()
export function install(Vue) {
	if (install.installed) return;
	install.installed = true;
	Vue.component('MyComponent', component); // <== CHANGE THIS
}

// Create module definition for Vue.use()
const plugin = {
	install,
};

// Auto-install when vue is found (eg. in browser via <script> tag)
let GlobalVue = null;
if (typeof window !== 'undefined') {
	GlobalVue = window.Vue;
} else if (typeof global !== 'undefined') {
	GlobalVue = global.Vue;
}
if (GlobalVue) {
	GlobalVue.use(plugin);
}

// To allow use as module (npm/webpack/etc.) export component
export default component; 
```

<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- Pages -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-3447513048440895"
     data-ad-slot="9229199209"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>

## ./build/rollup.config.js

Minimum setup for Rollup configuration.

```js
import commonjs from 'rollup-plugin-commonjs'; // Convert CommonJS modules to ES6
import vue from 'rollup-plugin-vue'; // Handle .vue SFC files
import buble from 'rollup-plugin-buble'; // Transpile/polyfill with reasonable browser support
export default {
    input: 'src/index.js', // Path relative to package.json
    output: {
        name: 'MyComponent', // CHANGE THIS
        exports: 'named',
    },
    plugins: [
        commonjs(),
        vue({
            css: true, // Dynamically inject css as a <style> tag
            compileTemplate: true, // Explicitly convert template to render function
        }),
        buble(), // Transpile to ES5
    ],
};
```

## ./src/my-component.vue

A sample component for the sake of demonstration.

```html
<template>
  <div class="container">This is an example component.</div>
</template>

<script>
export default {
  mounted() {
    console.log("Example component is mounted!");
  }
};
</script>

<style>
.container {
  background-color: red;
  padding: 10px;
  width: 100px;
  height: 100px;
  position: absolute;
}
</style>

```

# Serve

Install [@vue/cli](https://cli.vuejs.org/guide/installation.html) if you haven't done so. 

```
vue serve --open src/my-component.vue
```

# Build

```
yarn && yarn build
```

# Publish

```
# initial publish
npm publish --access public

# ...then bump patch version and publish
yarn version --patch && yarn publish
```

> If you don't have a NPM package account, you will need to [sign one up](https://www.npmjs.com/signup). Once you have signed up, you can use the `npm adduser` command to login from the terminal.

<style>
pre {
    background-color: #1c2022;
    color: white;
    padding: 10px;
    border-radius: 0.50rem;
    text-shadow: 0px 0px 1px black;
}
.highlight > pre {
    background-color: #f3f3f3;
    border-radius: 3px;
    line-height: 1.4;
    margin: 0 0 1rem;
    padding: 1rem;
    box-shadow: 0px 0px 11px #d6d1d1;
    text-shadow: 1px 1px 0px white;
    color: #383535;
}
</style>
<div id="disqus_thread"></div>

<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = window.location.href;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = 'publish-vue-component-as-npm-package-in-5-minutes'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
var disqus_config = function () {
  this.page.url = window.location.href;  // Replace PAGE_URL with your page's canonical URL variable
  this.page.identifier = 'publish-vue-component-as-npm-package-in-5-minutes'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};

(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://ansonc.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>