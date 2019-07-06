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

## Note: This is just for demo purposes. All the steps below will be using the default settings and lowest cost posibile. You should at least change your security settings for production.

# Step 1 Creating a Cluster

At the top, click **Services > ECS** or search **ECS**

![](https://gyazo.com/f34983033099847083fc02dfce3ca522.png)

Select **Create Cluster**

![](https://gyazo.com/1fdfe6eac4bdf26d8d172641178f4e7f.png)

On the **Select cluster template** page, click **EC@ Linux + Networking** and **Next Step**

![](https://gyazo.com/a097cf380df01bc42a54d13184e095f7.png)


On the **Configure cluster** page, choose your desired cluster name. 
- I'm going to choose **On-Demand instance** because it is cheaper. 
- **EC2 instance type** I will choose **t3.nano**
- **Number of instances** = 1
- **EBS storage** = 22 (That's the lowest you could get)
- Choose your [**Key pair**](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html) if you want to SSH into your instance. 

Finally, click **Create** at the bottom of the page.

![](https://gyazo.com/6fd54628a06b7c979ecc70310a4e35f3.gif)

It should take around 2 minutes (I have timed it) to complete. Now click on **View Cluster**.

![](https://gyazo.com/9cc4b367564eb96b5b0a0b7f9a1b47eb.gif)

If you go to the **ECS Instances tab**, you should see an instance there now. 

![](https://gyazo.com/d6d8027de8416efbb40301afbc49c384.gif)

However, the instance is empty right. We want to load our image into it. First, we will need to create a **Task Definition**.

Select **Task Definition** on the left side, click **Create new Task Definition**. and click **EC2**.

![](https://gyazo.com/bb7d6ba308e354d0a91407d3a1a96d43.gif)

Here is my task and container definitions
- Task Definition Name = wp
- Both **Task memory** and **Task CPU** are set to 256 (This must be less than the cluster memory)
- Under **Container Definition** Click **Add container**.
  - Container name = wp
  - Image = wordpress:5.2.2-php7.1-apache
  - Memory Limits: Hard Limit 128
  - Port mappings: 80:80
![](https://gyazo.com/4da49cddc8738349d0ca40b820d81845.gif)

Now go back to **Cluster**, go on **Tasks** tab and select **Run new Task**.
![](https://gyazo.com/c31365f85f2b8cdd35e9b012ebb4a3c3.png)

Here are my options:
- Launch type = EC2
- Task Defintion = wp:2
- Cluster = wp
- Number of tasks = 1

then click **Run Task**. 

If you go to **Tasks** tab now, you will see your task is running, and if you click in it, you would find your container External Link there.

Click on the link and you shall see this page.
![](https://gyazo.com/d69219127dd06c8db7f8fd8e66b7e91c.gif)

That's it.


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