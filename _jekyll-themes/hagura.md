---
title: Hagura
date: 2016-11-09
layout: post
image: hagura-jekyll-theme.png
desc: Hagura is a Kannada word for light-weight. It is very light and has very little CSS. But, I did not want to compromize the looks. The theme has very legible font style and distraction free layout.
link: http://webjeda.com/hagura/
dlink: https://github.com/sharu725/hagura/archive/master.zip
---

# Features:
Hagura is a theme made for blogs with long text paragraphs. Made to be easy on eyes as well. 

A switchable dark mode for low-light reading is available. 

Suitable fonts are selected for better readability. Since the theme is created for smartphone reading, the theme is very light so that it loads instantly on a slow data connection.

The theme comes with pre-installed **analytics**, **disqus** and **html compressor**. But make sure you change key parameters in the **_config.yml** file.

# Installation: 
Fork the ``master`` branch and delete ``gh-pages`` branch in it. This is important because ``gh-pages`` branch is used here only to host the blog. You should be using the master branch as the source and create a fresh ``gh-pages`` branch.

Watch my video on instlallation
<iframe class="video" src="https://www.youtube.com/embed/T2nx6tj-ZH4?rel=0?rel=0" frameborder="0" allowfullscreen></iframe>

## How to delete old **gh-pages** branch?
After forking the repository, click on **branches**.

![delete gh-pages branch](http://blog.webjeda.com/images/delete-github-branch.png)

Delete ``gh-pages`` branch.
![delete gh-pages branch](http://blog.webjeda.com/images/delete-github-branch-2.png)

You have to create a new ``gh-pages`` branch using the master branch. Go back to the forked repository and create ``gh-pages`` branch.

![create gh-pages branch](http://blog.webjeda.com/images/create-gh-pages-branch.JPG)

Now, go to settings and check the **Github Pages** section. You should see a URL where the blog is hosted.

This process will host the theme as a **Project Page**. You can also download the files for local development. 

The default theme will look like this

![webjeda hagura jekyll theme](http://webjeda.com/hagura/images/hagura-1.png){: .noborder}


This theme is responsive as well.

![webjeda hagura responsive jekyll theme](http://webjeda.com/hagura/images/hagura-responsive.png){: .noborder}
{: style="text-align:center"}

# Development
Make changes to the **master** branch and create a pull request. Do not use **gh-pages** branch as it is used to host the theme.

# License
MIT License

# Change Log

### Version 0.8
* Initial release with a reader-friendly layout.

[**Demo**]({{page.link}}){: .btn }
[**Download**]({{page.dlink}}){: .btn .red }