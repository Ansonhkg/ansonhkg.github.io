---
layout: post
title:  Setting up Laravel 5.6 with Docker Step by Step
date:   2017-09-20 04:07:59 +0100
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

## Updated 2018-02-19

# Prerequisite
- [Docker](https://www.docker.com/docker-windows)
- [HeidiSQL](https://www.heidisql.com/download.php)

	
# Install Laradock
1. Create a directory called `laravel5-6`
2. Open command prompt in this directory
3. Run `git clone https://github.com/Laradock/laradock.git`
4. Type `cd laradock` to enter laradock folder
5. Type `copy env-example .env` to create a new copy of env-example and rename it as `.env`
6. Open `.env` in **laradock** folder, change the application path to `APPLICATION=../backend`
7. Under `PHP_FPM`, enable the following packages:
```
PHP_FPM_INSTALL_XDEBUG=true
PHP_FPM_INSTALL_ZIP_ARCHIVE=true
PHP_FPM_INSTALL_MEMCACHED=true
PHP_FPM_INSTALL_MYSQLI=true
PHP_FPM_INSTALL_TOKENIZER=true
PHP_FPM_INSTALL_IMAGE_OPTIMIZERS=true
```
8. Go to `./laradock/nginx/sites/`
9. Create a copy of `app.conf.example` and rename it as `backend.conf`
10. Change everything named as `app` to `backend`
11. Leave the root as `root /var/www/public;`
12. Go to `./laradock` and open `docker-compose.yml`, find MariaDB Container
13. Under volumes, remove:
{% highlight linenos %}
	- ${DATA_SAVE_PATH}/mariadb:/var/lib/mysql
	- ${MARIADB_ENTRYPOINT_INITDB}:/docker-entrypoint-initdb.d
{% endhighlight %}

And replace it with `mariadb:/var/lib/mysql`

> The reason we are using mariadb instead of mysql is because it allows you to access the database container through MYSQL client. (HeidiSQL, etc.)

# Install Laravel5.5
1. In laradock folder, run `docker-compose up -d nginx mariadb` to start up containers
2. In laradock folder, run `docker-compose exec workspace bash` to enter the workspace container
3. Type `composer create-project --prefer-dist laravel/laravel .` Don't forger the dot (**.**) This will install Laravel project in the application path *(See Install Laradock: Step 5)*
4. Open `.env` and change `127.0.0.1` to `mariadb`
5. Change the `DB_DATABASE` and `DB_USERNAME` from `homestead` to `default` (Open `.env` in laradock folder, find `### MARIADB` and you should all the database details there
6. Type `php artisan migrate` to confirm the database is connected


# Hosts File
1. Open hosts file at `C:\Windows\System32\drivers\etc\hosts`
2. Add this line `127.0.0.1 backend.local`
6. Go to [backend.local/](http://backend.local/){:target="_blank"} on your browser

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