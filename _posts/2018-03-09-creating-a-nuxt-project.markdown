---
layout: post
title:  Creating a Nuxt.js project
date:   2018-03-09 17:42:00 +0100
categories: Web-Development
author: Anson Cheung
---

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

# Ongoing..

# 1) Installation
- Node.js (https://nodejs.org/en/)
- `npm install -g create-nuxt-app` (https://github.com/nuxt-community/create-nuxt-app)
- Now you can run `create-nuxt-app my-first-app` to initialize the project

# Notes
Some notes I would like to write down so that I can look up later.  Maybe this post is also helpful to you. 

# Pages, Routing & View
### Global styling - Fonts
- https://fonts.google.com
- Copy the font link, for example `<link href="https://fonts.googleapis.com/css?family=Lato" rel="stylesheet">`
- Open nuxt.config.js, add the link to 
```
link: [
    {rel: 'stylesheet', href: "https://fonts.googleapis.com/css?family=Lato"}
]
```
- This will be added to everywhere html generated by nuxt
- To use it, open your layout `default.vue`
- Specify in CSS, like the following

```
html{
    font-family: 'Lato', sans-serif;

}
```

### Using Tailwind in Vue Component

```
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

@tailwind preflight;

.btn-blue {
  @apply .bg-blue .text-white .font-bold .py-2 .px-4 .border-b-4 .border-blue-dark .rounded
}

.btn-blue:hover {
  @apply .bg-blue-light .border-blue
}

@tailwind utilities;

</style>
```

### Passing dynamic CSS
```
:style="{backgroundImage: 'url(' + thumbnail + ')'}
```

### Loading static assets using ~ alias
- `background-image: url('~assets/images/bg.jpg'); ` 

### Active nuxt-link router
```
a.nuxt-link-active{
    color: red;
}
```

# Handling Data

### Handling Error with Promise (remove callback as second argument)
```
return new Promise((resolve, reject) =>{
    resolve({...object})
    //OR
    reject(new Error())
}).then(data => {
    return data
}).catch(e => {
    context.error(e);
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
this.page.identifier = 'setting-up-laravel-5.5-with-docker-step-by-step'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
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