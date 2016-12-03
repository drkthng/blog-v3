---
title: Jekyll Issues aren't as Bad as You Think
desc: For a beginner, Jekyll may seem like a hypersensitive platform. A little deviation in the code will lead to an error or will not output the desired result. I have discussed some common issues that occur. 
author: sharathdt
tags: Jekyll 
image: common-jekyll-issues.png
layout: post
permalink: /jekyll-issues/
---


When I began using Jekyll I was almost pulled away from it because of the errors I used to get. The problem was not Jekyll being meticulous about its code but me being a jerk not go through the documentations! Most of us are those guys who run a nuclear reactor without knowing how it works.

## The early Jekyll issues
Let's begin with the basics. You've heard about Jekyll and you're all excited to create a blog. You find a theme, say [Hyde](https://github.com/poole/hyde){: target="_blank" rel="nofollow"}, you fork it, delete ``gh-pages``, create new ``gh-pages`` branch, check the **settings** and you get something like this.

Read: [How create a beautiful Jekyll Blog](/create-jekyll-blog/){: target="_blank"}

![Your site is using the relative_permalinks configuration option](/images/jekyll-build-issues.PNG){: .noborder}

What?!! As per the tutorial, you should have seen a URL but you are seeing an error!
{: .r}

This is because some Jekyll themes like [Hyde](http://hyde.getpoole.com){: target="_blank" rel="nofollow"} are not yet updated. They should have removed ``relative_permalinks`` from **_config.yml** since it is depricated. But theme developers could be busy with other things. 


* Do not remove this line (it will not be displayed) 
{:toc}


## The second Jekyll error
Ok, now you know what to do. Go back to the repository, open **_config.yml** and delete this line.

``relative_permalinks: true``

Well done. Now you check the settings page again and can't wait anymore to get the website live but...

![The CNAME is already taken jekyll issue](/images/jekyll-build-issues-cname-already-taken.PNG){: .noborder}


{% include adsense-inside-post.html %}


Hmm., this is no biggie. You just have to delete the CNAME file in the repository. You delete it and check the setting page again. For a change, you see a URL!


![settings URL jekyll issue](/images/jekyll-issues-settings-url.PNG){: .noborder}

Now, you click on it to check the website but..

## Jekyll no style issue

You see this

![jekyll no style issue](/images/jekyll-issues-no-style.PNG)

which was supposed to look like this!

![jekyll no style issue](/images/jekyll-issues-with-style.PNG)

This is where most of us give up. We think this is never going to work. We all have seen this. Haven't we? 

A careful observation tells us that the problem is just with the assets(css, js, images). They are not loading. Why?
{: .y}

Right click on it and view pages source

![jekyll no style issue view source](/images/jekyll-issues-no-style-view-source.PNG)

Click on one if those stylesheets and you will get a **404** error. But observe the URL of that 404 page carefully.

``https://username.github.io/public/css/poole.css`` 

This URL is not the right one. The right one for Hyde theme is this

``https://username.github.io/hyde/public/css/poole.css``

Where did that **/hyde** go?

## Jekyll baseurl issue

So the problem is that your Jekyll website is loading assets(css, js, images) from the root of your GitHub account whereas it should have loaded it from the particular repository, in our case **hyde**.

So how do we tell it to load assets from the hyde repository?

That's where ``baseurl`` comes into the picture.

Open the configuration file **_config.yml** and check for ``baseurl``. 

{% highlight yml %}
# Setup
title:            Hyde
tagline:          'A Jekyll theme'
description:      'A brazen two-column <a href="http://jekyllrb.com" target="_blank">Jekyll</a> theme that pairs a prominent sidebar with uncomplicated content. Made by <a href="https://twitter.com/mdo" target="_blank">@mdo</a>.'
url:              http://hyde.getpoole.com
baseurl:          /
{% endhighlight %}

Baseurl is just a **``/``** which should have been **``/hyde/``** or whatever the name your repository has.

Edit it to **/hyde/** and check the website URL again. You should see the website with it's full style and functionality!

Learning a little more about ``baseurl`` wouldn't hurt. Parker Moore(Jekyll developer) himself has posted this [article](https://byparker.com/blog/2014/clearing-up-confusion-around-baseurl/){: target="_blank"} to clear the doubts.
{: .g}

Now that the problem is resolved, you start writing your first blog post and try to see it in action but it doesn't show up!


## Jekyll not showing images
This problem is mostly faced by new developers who try to host their website on Github Pages. They check the website files locally and everything works fine but when they push it to Github, they see this 

![jekyll not showing images ](/images/jekyll-images-not-showing.PNG)

Which was supposed to look like this.

![jekyll not showing images ](/images/jekyll-images-not-showing-2.jpg)


The problem is simple. For some reason the image is not getting detected. But we know that the image is present. Just inspect the image(error image) and see why it is not showing up.

![jekyll images not displaying  ](/images/jekyll-image-not-showing.png)

Inspecting the code might relveal something like this

{% highlight yml %}
<div>
<img src="img/some-image.jpg" class="img-responsive" alt="">
</div>
{% endhighlight %}

What we observe here is that the image path is from the root but Github Pages will not recognize this. Adding a **/** in the beginning of the path will solve the error most of the times but that may not be enough.

You may have to specify that the root of the folder is your repository. If your repository name is **repo** then the image path should be ``/repo/img/some-image.jpg``. This should solve the error.

For Jekyll users, ``/repo`` is actually **baseurl**. So if you have mentioned ``baseurl: /repo`` in the **_config.yml** file then you can change the path to ``{% raw %}{{site.baseurl}}/img/some-img.jpg{% endraw %}``


## Jekyll post not getting generated

There are some reasons for this. Make sure you did not get any page build error. If so, read [How to deal with page build errors](/page-build-error/){: target="_blank"}. Most of the times it will be a markdown syntax error.

### Check 1: Location of post file
Jekyll treats a file as a post if it is inside **_posts** directory. If your post is somewhere else then move it inside **_posts** directory.

### Check 2: Incorrect post title
Jekyll posts should be named in this format ``YYYY-MM-DD-title.MARKUP``. Check if your posts follow this pattern.

{% include adsense-inside-post.html %}

### Check 3: Post has a future date
If you have not mentioned any timezone in the configuration, then Jekyll sets it to your operating system timezone. Sometimes you may give today's date in the filename like ``{{ site.time | date: '%Y-%m-%d' }}-some-title.md``(yes, today!) but based on timezone the date could be in the future. Jekyll will not show it today. Comeback and check tomorrow. Or if you can't wait then add this line to the post's front matter to make future posts visible - ``future: true``.

### Check 4: Title has **:** character
If your title has ``:`` as a string then Jekyll throws an error. One way to solve this is by removing it or replacing it by ``&#58;``. The best way to solve this is by quoting the title with apostrophes.

{% highlight yml %}
---
title: 'Interesting stuff: Explained'
layout: post
---
{% endhighlight %}

### Check 4: Front matter has published: false
If a post contains ``published: false`` in the front matter, then that post will not show up anywhere. Either remove it or change it to ``published: true`` to see the post in the output.

One of those should solve the issue.

## Using Jekyll code blocks in Jekyll

I have observed this in many new Jekyll users. Whenever they are tring to show a Liquid syntax code block in a post, they either use some other symbol for curly braces or they put screenshots of the code. 

This is not necessary. You can actually show Liquid syntax (or Jekyll code as some might call it) as is in a Jekyll website. 

Jekyll has default syntax highlighting for many programming languages. But for Liquid syntax, the normal procedure would not work.

For example, This code block shows the URL of the current page.
{% highlight yml %}
{{ page.title }}
{% endhighlight %}

But what you wanted to show was this

{% highlight yml %}{% raw %}
{{ page.title }}
{% endraw %}{% endhighlight %}


So in order to use Liquid Syntax, you should use {&#x0025; raw &#x0025;} and {&#x0025; endraw &#x0025;} like this,

{% highlight yml %}
{&#x0025; raw &#x0025;}<br />
{% raw %}{{ page.title }}{% endraw %}<br />
{&#x0025; endraw &#x0025;}
{% endhighlight %}

When you use these tags, the code is shown as it is without executing it.

{% include adsense-inside-post-2.html %}

## Jekyll on windows
There were many issues with Jekyll running on windows. The major one being installing Jekyll on windows. Most of the issues are getting fixed on a good pace. Also, windows has a package manager which is new for windows users I guess(at least for me). 

Here is a [list of software packages](https://chocolatey.org/packages){: target="_blank" rel="nofollow"} that you can install by entering one line of code. Chocolatey checks for a suitable version of the software. and installs it on your desktop.


![jekyll on windows chocolatey](/images/chocolatey-windows-jekyll.PNG)

### Install Jekyll on windows
It is easy to install Jekyll on windows now.

**1. Install [Chocolatey](https://chocolatey.org/install){: target="_blank" rel="nofollow"}:** A package manager for windows.

**2. Install Ruby using Chocolatey:** Run ``choco install ruby -y``


**3. Install Jekyll:** Run ``gem install jekyll``

That should do it. If you want a GUI installation process then follow this [link](http://jekyll-windows.juthilo.com/1-ruby-and-devkit/){: target="_blank" rel="nofollow"}

A video on some basic Jekyll issues
<iframe class="video" src="https://www.youtube.com/embed/bty7LHm14CA?rel=0" frameborder="0" allowfullscreen></iframe>

These are the ones I can think of right now, feel free to suggest other issues in the comment section.

Thanks for reading!