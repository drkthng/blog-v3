---
title: Jekyll's got a new GUI for local editing!
desc: Jekyll-admin is a GUI for editing Jekyll website or blog. It has its ups and downs. It is still in the early stages of its development. I have tried the initial release and here is my review. 
author: sharathdt
tags: Jekyll 
image: jekyll-admin-tutorial.png
img-src: "http://www.freepik.com/free-vector/typewriter-illustration-vector_756501.htm"
img-src-name: Design by Freepik
layout: post
permalink: "/jekyll-admin/"
---

## What is jekyll-admin
[Jekyll admin](https://github.com/jekyll/jekyll-admin){: target="_blank"} is a Ruby gem for Jekyll which provides a local user interface for editing posts and pages. By the time of writing this article, the version is 0.1.0.

If you have [ever used WordPress](/why-jekyll-over-wordpress/){: target="_blank"} then you may have noticed that editing post was a little easier than Jekyll because of the user interface(UI). You can drop in images, html code blocks, you see the changes right away with preview option etc.. WYSIWYG kind of editors are good for a non-coder because he/she knows what will be the output.

* Do not remove this line (it will not be displayed) 
{:toc}

Jekyll is trying to fill that gap of not having a UI by jekyll-admin. But it has a long way to go. With the current build, it is nowhere close to usable.


## Why Jekyll-admin?
Jekyll was considered to be not so non-coder friendly. Because to take advantage of the features of a Jekyll blog, one should have some basic coding knowledge or at least knows how to manipulate the present code.

I think Jekyll is trying to solve this problem. But to run Jekyll locally you need to install Ruby and then install Jekyll. For a non-coder, even this process could be tough. Making things simpler is important to reach more people. That's what worked out for Apple in the case of iPhones.

In [my videos]({{site.youtube}}){: target="_blank"}, so far I haven't discussed anything about CLI. If you do not want use Jekyll locally then you can make use of these videos and use an online editor like [Prose](http://prose.io) to edit your posts and pages.

But if you are already using Jekyll locally and pushing changes to remote host(Github Pages or another service) then this could be a better option to edit your posts.

An added advantage is that when I edit posts using jekyll-admin, I can make use of browser add-ons like Grammarly to check my spelling which is not possible while editing posts on an IDE.

## Usage
The first thing you should be doing is to install the jekyll-admin gem in your project. Open command line interface, navigate to your project and then enter these commands.

Install jekyll-admin. This will take a while.
{% highlight ruby %}
gem install jekyll-admin
{% endhighlight %}

Mention the gem in your configuration file **_config.yml**.
{% highlight ruby %}
gem: [jekyll-admin]
{% endhighlight %}

Now serve Jekyll locally as usual.
{% highlight ruby %}
jekyll serve
{% endhighlight %}

Now, your admin page should be available at the below URL

``http://127.0.0.1:4000/admin``

{% include adsense-inside-post.html %}


You should see something like this.

![jekyll admin](/images/jekyll-admin.png){: .noborder}

## Features
Most of the basic features are available in this initial release. I'm hoping to see more in the next versions.

1. Post
2. Page
3. Collections
4. Data files
5. Static files
6. Configuration

All these things can be edited. That means you can edit post and pages directly here without opening the whole project with an IDE like Brackets.

Posts and pages can be edited and previewed while editing. This is very handy for new Jekyll users.

![jekyll admin edit post page](/images/jekyll-admin-edit-post.png){: .noborder}

Here you can write the post, style it, insert images, links, blockquotes etc.. You can also add Front Matter using metadata field. There is an option to split the screen while editing to see the preview.

![jekyll admin preview post page](/images/jekyll-admin-preview-post.png)

Along with posts and pages, you can also edit collections. I wasn't expecting it to detect the collection I had but it did which is really cool. The **static files** directory will have all the images, css, and js. The **configuration** option is nothing but your _config.yml file. 


## What is missing?

### Autosave
I tried to edit this post using jekyll-admin but I got frustrated because when I navigate to some other tab and come back to the particular post I was editing, all I wrote is gone! This happened twice and I gave up. An auto-save option is a must at least for me to use it.

### Drag and drop image upload
This feature will appear sooner or later. Currently, when I click on image icon it shows markdown code where I can enter the image path. But what I(and most users) want is an option where I can drop an image from anywhere on my local drive to the post and it should automatically upload it to images folder of my project and insert it into the post.

I like how WordPress handles image upload. You can drag and drop an image anywhere inside a post and it will take care of the rest.

### Multiple options in metadata
Currently, metadata is an empty field where we have to fill 'title', 'layout' and other front matter and give it a value. It would be great if Jekyll can offer some basic metadata options by default which can be edited.

{% include adsense-inside-post-2.html %}

### Default metadata for new posts and pages
Here metadata is nothing but front matter. I have so many of them. Title, description, layout, tags, permalink etc.. So I want to see an option where I can choose the default metadata values that automatically appear in every new post.

Even better if it can detect the metadata fields from previous posts!
{: .g}

### Code insert option
I don't know why they haven't included code insert option. I want an option similar to the one in StackOverflow. Maybe in the future versions, it can have an options to let me choose which programming language I want to highlight.

One last thing I want to mention is that when I upload a static file, say an image, it says that it was uploaded successfully but when I check inside the project the file is nowhere to be found. This probably is a bug which will be fixed in the coming release.

## Conclusion
Even though the initial version lacks so many things, I really appreciate the initiative from Jekyll team. Contributors will definitely improve its performance and usability. I will definitely suggest my clients to use it once it is stable and can be run from a desktop icon instead of a command line!