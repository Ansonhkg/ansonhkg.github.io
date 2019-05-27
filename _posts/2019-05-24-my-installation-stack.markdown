---
layout: post
title:  My Current Development Stack
date:   2019-05-24 21:50:00 +0100
categories: Web-Development
author: Anson Cheung
---

# My Current Development Stack
- Vue.js (Nuxt framework)
- ExpressJS (API Server that connects to multiple data sources)
- Microsoft SQL Server 2017 (A legacy server that stores 700+ millions worth of data but performs very slow search due to high search request). 
- Docker (Hosting the following) 
  - Elasticsearch (3 Master nodes, 2 Client nodes, 2 Data Nodes indexing 12 companies, indexing 700+ millions documents) ![][datasize]
  - Redis Service (Cache calculated Elasticsearch result)
  - Logstash (Run queries from SQL Server and send it to Elasticsearch)
  - Kibana

- Microsoft Azure VM

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = window.location.href;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = 'setting-up-nuxt-with-tailwind-css'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
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