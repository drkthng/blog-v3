---
title: Online CV
date: 2016-07-28
layout: post
image: online-cv-jekyll-theme.png
desc: Online CV is a minimal responsive Jekyll Theme to host a resume(CV) online.
link: http://webjeda.com/online-cv/
dlink: https://github.com/sharu725/online-cv/archive/master.zip
---



# Features

## Customizable theme
The theme can be customized just by changing few variables in **_config.yml** file.

## Easy to edit the information
All the info-blocks used are sorted into separate items. So editing them would be very easy.

# Installation

Here is a video guide

<iframe class="video" src="https://www.youtube.com/embed/T2nx6tj-ZH4" frameborder="0" allowfullscreen></iframe>

Fork the ``master`` branch and delete ``gh-pages`` branch in it. This is important because ``gh-pages`` branch is used here only to host the blog. You should be using the master branch as the source and create a fresh ``gh-pages`` branch.

## How to delete old **gh-pages** branch?
After forking the repository, click on **branches**.


![delete gh-pages branch]({{site.baseurl}}/images/delete-github-branch.png)

Delete ``gh-pages`` branch.
![delete gh-pages branch]({{site.baseurl}}/images/delete-github-branch-2.png)

You have to create a new ``gh-pages`` branch using the master branch. Go back to the forked repository and create ``gh-pages`` branch.

![create gh-pages branch]({{site.baseurl}}/images/create-gh-pages-branch.JPG){: style="border: 1px solid #eee" }

Now, go to settings and check the **Github Pages** section. You should see a URL where the blog is hosted.

{% include adsense-inside-post.html %}

This process will host the theme as a **Project Page**. You can also download the files for local development. 

Default theme will look like this

![online cv Jekyll theme](https://raw.githubusercontent.com/sharu725/online-cv/master/assets/images/online-cv-jekyll-theme.png){: .noborder}

This theme is responsive.

![online cv responsive Jekyll theme](https://github.com/sharu725/online-cv/raw/master/assets/images/online-cv-responsive-jekyll-theme.png){: .noborder}
{:  style="text-align:center" }

# Customization

## Theme
The of different color schemes that can be achieved by changing style variables in the **_config.yml** file.

{% highlight yaml %}

# Enable one of these styles by removing #
#style: styles-2
style: styles-3
#style: styles-4
#style: styles-5
#style: styles-6

{% endhighlight %}

![online cv Jekyll theme](https://github.com/sharu725/online-cv/raw/master/assets/images/online-cv-jekyll-theme-2.png){: .noborder}

Remember, while developing locally, every change you make in **_config.yml** is applied only if you restart ``jekyll serve`` process.

# Development
Make changes to the **master** branch and create a pull request. Do not use **gh-pages** branch as it is used to host the theme.

# License
MIT License

[**Demo**]({{page.link}}){: .btn }
[**Repository**]({{page.dlink | remove: 'archive/master.zip'}}){: .btn .green}
[**Download**]({{page.dlink}}){: .btn .red }