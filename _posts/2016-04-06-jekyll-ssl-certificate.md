---
title: SSL certificate (https) for Jekyll
desc: Https has an advantage in SEO over http. It is easy to set up SSL for Jekyll using CloudFlare. Learn how to get a free SSL certificate for your Jekyll blog. Also, find out the advantages and disadvantages of using SSL on your website.
keywords: 
author: sharathdt
tags: Jekyll SEO Github-Pages 
image: ssl-jekyll.png
permalink: /jekyll-ssl/
layout: post
---


## Why should anyone use SSL?
{: .clear}
SSL (Secure Socket Layer) basically provides a secure connection between the client(web browser) and server(website). It avoids eavesdropping, man-in-the-middle attack etc., Bottom line is - A user can browse your website without worrying about someone stealing personal information.



* Do not remove this line (it will not be displayed) 
{:toc}


On August 06 2014 Google announced that [https will be considered for ranking signal](https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html){:rel='nofollow'}{:target="_blank"}. They took this measure to keep everybody safe over the web. So by using SSL you can improve your website ranking and your users will feel safe and trust the product or service you are providing.


## Why I'm not using SSL on this Jekyll blog?
![Jekyll and GitHub pages https](/images/nallikayi-articles-github-pages-ssl.jpg)
{: .right}

**Update: I did not use SSL for some reasons that I have mentioned below. Currently I'm using SSL.**

I'm using SSL on [Nallikayi Articles](https://articles.nallikayi.com){:target="_blank"} but not on other websites. Why did I do so? If SSL is good for SEO, why didn't I use it on all my websites? Especially, why didn't I use it on this blog?! The reasons are as follows,


### Adsense
{: .clear}
I use Adsense for monetizing this blog. If I were to secure this blog with SSL, I should not request any data from a http server. Everything should be https! But, most of the ads on Adsense are from a http source which is not acceptable for an SSL certified website.

{% include adsense-inside-post.html %}

Google detects whether your website has an SSL certificate or not and serves ads accordingly. If I activate SSL in my Jekyll blog, Google will filter only https ads and serve it on my website. This way I may miss some high paying ads.

### Performance
Website loading speed is my main concern. I want it to be fast; really fast. Activating SSL would slow down my Jekyll blog a little due to TLS handshaking which is a process that the browser and server follow to decide how to communicate and create a secured connection.

Google also announced that they were using page load time as a factor in search engine rankings. SSL and page-load time conflict with each other(a little bit). Anyway, the load time will be a little more than what it used to be. So if speed is not your priority then you can always go ahead and use SSL.


<div class="warning">
<h3>Update Aug 2016</h3>
<p>After considering all the advantages and disadvantages of SSL, I'm going with secure SSL. Google is trying hard to push web developers to move to <code>https</code>. That makes sense because everyone wants their information to be safe on the internet.</p>
</div>




## How to get SSL on Jekyll?

If your website or Jekyll blog URL is in the format ```username.github.io``` then you can use https right away just by enforcing it. But before you do that, verify if ```https://username.github.io``` renders the same thing and you see a green padlock before the URL.

If it works but you do not see a green padlock then the reason must be that your website is requesting something from a non-secure (http) server. Read [warning](#warning-1) to solve this.

### Enforce https
If you are not using a custom domain name then you can use the **Enforce HTTPS** option found in settings page. It redirects the website to https from server side which is better than doing it from client side.

![Github Pages enforce https](/images/github-pages-enforce-https.png)

If you are using a custom doamin then this option will not be available. You have to skip to this [step](#ssl-on-custom-domain).

If you want to do it from the client side(not recommended) then use this JavaScript code at the top of your website to redirect to https. Change **username** to your GitHub username.

{% highlight js %}
var host = "username.github.io";
if ((host == window.location.host) && (window.location.protocol != "https:"))
    window.location.protocol = "https";
{% endhighlight %}


### Change Canonical URL to https
You should let search engines read your content only in https site. Use canonical URL in the head section.

{% highlight html %}
<link rel="canonical" href="https://username.github.io" />
{% endhighlight %}

for Jekyll, it should be 
{% highlight html %}{% raw %}
<link rel="canonical" href="{{ site.url }}{{ page.url }}" />
{% endraw %}{% endhighlight %}

Make sure that the **url** is https in **_config.yml**. Also use ```enforce_ssl``` parameter.

{% highlight yml %}
url: https://username.github.io
enforce_ssl: username.github.io
{% endhighlight %}

This way, there will be no trace of your **http** website anywhere on the internet even though it works.

{% include adsense-inside-post-2.html %}

## SSL on custom domain
If you are using a custom domain, say ```yoursite.com``` then you may have to use a different approach. If enforcing works then great! Otherwise follow the procedure given below.

### Step 1: Migrate DNS to CloudFlare
[CloudFlare](https://www.cloudflare.com/){:rel='nofollow'}{:target="_blank"} is a CDN service which offers pretty decent service on free account. I'm using CloudFlare for all my websites. CDN provides local copies of the website through a nearby server so that there is no delay in website loading. 

It also has other advantages like handling DNS, analytics, providing SSL certificate - flexible and paid, firewall, speed optimization, caching etc., Watch the video on their website to know how it works. And it doesn't matter where you have bought your domain and where you are hosting your website.

![Add a site cloudflare jekyll ssl](/images/add-site-cloudflare-jekyll-ssl.jpg){: .large .left}

Among these, we are concentrating only on DNS handling. So before we begin to create an account in CloudFlare. Now select **Add site** option. Now enter your domain and click on **Begin scan**.

Once the scanning is done, click on **Continue to setup** where you will see an option to verify all your DNS records. You don't have to change anything here. click on **Continue**.

Now select a package that suits your requirement. I would suggest you to try the free version first and then upgrade if you like their service.
{: .clear}

![change DNS CloudFlare Jekyll GitHub ssl](/images/change-dns-cloudflare-jekyll-github-ssl.jpg)
{: .right .half}
Now is the crucial part. You have to change the name servers (NS31.DOMAINCONTROL.COM) in your domain registrar to the following or whichever is provided to you by CloudFlare.

{% highlight css %}
dan.ns.cloudflare.com

may.ns.cloudflare.com
{% endhighlight %}

You have to login to your domain registrar and add these custom name servers. Once it is done, click on **Continue**. It may take a while to reflect the changes but once it is successfully done, you will see a **Status: Active** message on CloudFlare.


### Step 2: Use 'Flexible SSL'
{: .clear}

![cloudflare flexible ssl jekyll](/images/cloudflare-flexible-ssl-jekyll.jpg)
{: .half .left}
Now navigate to **Crypto** option in CloudFlare. You should see an option called **SSL**. In the drop-down menu select **Flexible**. This is all the changes we need to do in the server end.


### Step 3: Changes to be made in CloudFlare
{: .clear}

![cloudflare https redirect page rule jekyll ssl](/images/cloudflare-https-redirect-page-rule-jekyll-ssl.png)
{: .right .half}
Use **Page-rule** to redirect http to https. Use * symbol to create dynamic patterns that match many URLs.
<div class="clear"></div>

If you prefer to redirect in the website then use the below JavaScript code. I would recommend using CloudFlare Page-rule instead of this.

Follow the enforcing procedure.

Use this JavaScript at the top of the default template. Replace **yoursite** with your domain name.
{% highlight js %}
var host = "yoursite.com";
if ((host == window.location.host) && (window.location.protocol != "https:"))
   window.location.protocol = "https";
{% endhighlight %}

### Step 4: Changes to be made in the website

As I mentioned earlier now your website is ready for SSL. Check again if the https link is working(all pages of the website). If not troubleshoot using the [warning](#warning-1).


Use canonical URL in the head section to let search engines know that you are using https. 
{: .clear}
{% highlight html %}{% raw %}
<link rel="canonical" href="{{ site.url }}{{ page.url }}" />
{% endraw %}{% endhighlight %}

Make sure that the **url** is https in **_config.yml** and use ```enforce_ssl``` parameter

{% highlight yml %}
url: https://yoursite.com
enforce_ssl: yoursite.com
{% endhighlight %}


<div class="warning" id="warning-1">
<h3>Warning</h3>
<p>All the resources that are requested by a <strong>ssl</strong> activated website should also be secured. That is, if you request any file with a  <strong>http</strong> link then the green padlock will not appear. In order to avoid that use relative url. For example, instead of <code>http://webjeda.css</code> use <code>//webjeda.css</code></p>
</div>

## Conclusion
Flexible SSL is not a complete solution for security since it is provided by ClouFlare. If someone can hack into CloudFlare then they can steal information from your users! Let's hope that doesn't happen. Since we are just using it for SEO ranking, we are good. If you are looking for complete security then you can buy SSL certificate for your website. It is good to buy SSL certificate if you are selling something on your website which has payment-gateway integrated.

I hope that helped you set up SSL on your website. Ask any doubts you have through comments. Do not forget to subscribe.

Thanks for reading!