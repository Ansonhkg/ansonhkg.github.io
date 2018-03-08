---
layout: post
title:  Creating a Tailwind Project with Browser Sync
date:   2018-03-05 17:20:00 +0100
categories: Web-Development Web-Design
author: Anson Cheung
---

# Dev Stack
- [TailWind](https://tailwindcss.com/)
- [Browser Sync](https://browsersync.io/)

	
# 1) Tailwind CSS Webpack Starter Project Installation
- Clone git repository to your current folder `git clone https://github.com/tailwindcss/webpack-starter.git .`
- Run `yarn`
- Run `".\node_modules\.bin\webpack\" --watch`

# 2) Install Browser Sync
- Run `yarn add --dev browser-sync-webpack-plugin`
- Run `yarn add browser-sync`
> If running on Windows CMD, replace forward (/) slash with backward (\). ".\node_modules\.."

# 3) Configure Webpack
- Open `webpack.config.js`
- Add `const BrowserSyncPlugin = require('browser-sync-webpack-plugin')` at the header
- In the `plugins` array, add 
```
new BrowserSyncPlugin({
      host: 'localhost',
      port: 3000,
      server: {baseDir: ['./']},
      files: ['./*.html']
    })
```

# 4) Finally
- Run `yarn webpack --watch` to start watching file...

# Demos
- [http://ansoncheung.me/WBP_Clone_Tailwindcss](http://ansoncheung.me/WBP_Clone_Tailwindcss)

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