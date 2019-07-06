---
layout: post
title:  How to create a vertically and horizontally centered container in CSS
date:   2019-05-27 00:00:00 +0100
categories: Web-Development Snippet
author: Anson Cheung
---

## Tailwind.css
```html
<div class="flex justify-center items-center">
    <div class="m-auto">
        {{ text }}
    </div>
</div>
```
## Vanilla CSS

HTML
```html
<div class="wrapper">
    <div class="content">
        {{ text }}
    </div>
</div>
```

CSS
```css
.wrapper{
  /* You can change your style and height */
  background-color:white;
  height:500px;
  
  /* But the structure has to be like this */
  display: flex;
  justify-content:center;
  align-items: center;
}

.content{
  margin:auto;
}

```

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = window.location.href;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = 'how-to-create-a-vertically-and-horizontally-centered-container-in-css'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
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