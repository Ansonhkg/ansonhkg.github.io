---
layout: post
title:  Basic Licensing Logic in JS
date:   2019-05-24 21:50:00 +0100
categories: Web-Development
author: Anson Cheung
---

# Basic Licensing Logic in JS
```js
const LICENSED_SITES = {
  'localhost':{

  },
  '127.0.0.1':{

  },
  'deliveroo.fe-ltd.co.uk.ansoncheung.me':{

  }
}

var SITENAMES = Object.keys(LICENSED_SITES)
    
var requestOriginAddr = 'deliveroo.fe-ltd.co.uk.ansoncheung.me'

var origin = requestOriginAddr.replace(/http:\/\/|https:\/\//, '')

var isLicensed = SITENAMES.indexOf(origin) !== -1

console.log(requestOriginAddr + ' is ' + (isLicensed ? 'licensed' : 'NOT licensed'))

```

<iframe src="https://codesandbox.io/embed/trusting-star-gx61j?expanddevtools=1&fontsize=14&module=%2Fsrc%2Flicense.js" title="trusting-star-gx61j" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = window.location.href;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = 'basic-licensing-logic-in-js'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
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

[datasize]:https://image.prntscr.com/image/qwJx0S5qQKaWebNNr2bxIw.png