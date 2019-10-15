---
layout: post
title: An ultra minimal guide to deploy Nuxt SSR
date: 2019-10-15 13:53:00 +0100
categories: Web-Development Vue Javascript Nuxt SSR
author: Anson Cheung
---

# An Ultra Minimal Guide to Deploy Nuxt SSR

This short tutorial will be using [Zeit Now](https://zeit.co) to deploy Nuxt SSR application.

- [An Ultra Minimal Guide to Deploy Nuxt SSR](#an-ultra-minimal-guide-to-deploy-nuxt-ssr)
- [Expected Usage](#expected-usage)
- [Steps](#steps)
  - [Create a zeit account](#create-a-zeit-account)
  - [Install Zeit Now](#install-zeit-now)
  - [Login via terminal](#login-via-terminal)
  - [Create Nuxt App](#create-nuxt-app)
  - [Change build directory (IMPORTANT)](#change-build-directory-important)
  - [Generate](#generate)
- [Finally, deploy.](#finally-deploy)

# Expected Usage

In your Nuxt project folder, run

```
now
```

It will deploy to Zeit Now server and generate a link for you.

Repo: https://github.com/Ansonhkg/vue-ssr-deploy-sample

# Steps

## Create a zeit account

https://zeit.co/signup

## Install Zeit Now

```
npm i -g now
```

## Login via terminal

```
now login
```

## Create Nuxt App

```
npx create-nuxt-app my-app
```

## Change build directory (IMPORTANT)

Open `nuxt.config.js`, and add the following.

```javascript
export default {
  generate: {
    dir: "public"
  }
};
```

## Generate

> When launching `nuxt generate` or calling `nuxt.generate()`, Nuxt.js will use the configuration defined in the `generate` property.

Run the following command, t should create a directory called `public` in your project directory.

```
yarn generate
```

Check if `public` directory is indeed generated. If not, there's something wrong.

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

# Finally, deploy.

Run

```
now

## for future deployment run
now --prod
```

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
  this.page.identifier = 'an-ultra-minimal-guide-to-deploy-nuxt-ssr-app'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};

(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://ansonc.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>

<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
