---
layout: post
title:  How to deploy a simple AWS application on AWS
date:   2019-07-06 00:00:00 +0100
categories: Web-Development DevOps
author: Anson Cheung
---

# How to deploy a simple docker application to AWS (2019)

# Prerequisite
- An AWS account
- Prepare your docker image. In this example I will be using `wordpress:5.2.2-php7.1-apache`

# Step 1 Creating a Cluster
![](https://gyazo.com/f34983033099847083fc02dfce3ca522)


<div id="disqus_thread"></div>

<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = window.location.href;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = 'how-to-deploy-a-simple-docker-application-on-aws'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
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