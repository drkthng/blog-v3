---
title: Page Build Errors on Jekyll?! - Solve them!
desc: Page build errors are very common even for an experienced developer because there are many things that can go wrong with Jekyll or Github Pages. I have discussed a better way to deal with those errors here.
author: sharathdt
tags: Github-Pages Jekyll 
image: jekyll-build-error-troubleshooting.png
img-src: "http://www.freepik.com/free-vector/building-a-city-illustration-in-flat-design_899114.htm"
img-src-name: Design by Freepik
layout: post
permalink: /page-build-error/
---


This post is a summary of years of my experience using Jekyll and Github Pages. I have seen too many errors in these years. I had to face one just yesterday. I thought maybe others are facing this kind if issues as well. So I'm writing this article on how to deal with it.

## Why page build errors happen?
Page build error happens for a number of reasons. A missing HTML tag, missing CSS curly brackets, missing endfor or endif liquid syntax, markdown syntax error and sometimes even for using a tab instead of space in _config.yml file!

* Do not remove this line (it will not be displayed) 
{:toc}

Usually, page build error happens when you push a new post or you change the design of your blog. Sometimes page build error happens just after a simple change and you have no idea what went wrong.

{% include adsense-inside-post.html %}

## The first thing to do when an error happens.
There is nothing to panic over a **page build error** because your site will retain its last push but will not allow any more change to happen until you solve the error.

This is where people mess things up. They assume that the last commit was the reason and they may reset the branch to the previous commit. This will solve the problem if your last commit had error but what if your last one isn't the culprit?!

What if you are using something that is deprecated? So in such cases, it is a little hard to figure out what went wrong. But do not try to change too many things like I did one time which caused this downtime.
{: .r}

![jekyll page build error downtime](/images/jekyll-pagebuild-error-downtime.png)

## How to identify the error
Github sends you an email in most cases when a page build error happens. Most of the times it will have the details on what went wrong. If you do not receive one then you can check the settings page in your website repository for any error messages.

![Jekyll page build error](/images/jekyll-page-build-error-screenshot.PNG){: .noborder }

I'm posting some of the emails I have received over the years

Markdown syntax error:

{% highlight html %}{% raw %}
The page build failed with the following error:

The file `_posts/2012-02-06-whats-jekyll.md/#excerpt` contains syntax errors. For more information, see https://help.github.com/articles/page-build-failed-markdown-errors.

If you have any questions please contact us at https://github.com/contact.
{% endraw %}{% endhighlight %}

CSS error:

{% highlight html %}{% raw %}
The page build failed with the following error:

The file `style.scss` contains syntax errors. For more information, see https://help.github.com/articles/page-build-failed-markdown-errors.

If you have any questions please contact us at https://github.com/contact.
{% endraw %}{% endhighlight %}


Liquid syntax error:
{% highlight html %}{% raw %}
The page build failed with the following error:

The tag `{%` in `_posts/2014-10-13-CCNA.md` was not properly closed with `%}`. For more information, see https://help.github.com/articles/page-build-failed-tag-not-properly-terminated.

If you have any questions please contact us at https://github.com/contact.
{% endraw %}{% endhighlight %}


Symlink error:
{% highlight html %}{% raw %}
The page build failed with the following error:

A file was included in `_layouts/post.html` that is a symlink or does not exist in your `_includes` directory. For more information, see https://help.github.com/articles/page-build-failed-file-is-a-symlink.

If you have any questions you can contact us by replying to this email.
{% endraw %}{% endhighlight %}

Config error after Jekyll 3.0 update:
{% highlight html %}{% raw %}
The page build failed with the following error:

You have an error on line 24 of your `_config.yml` file. For more information, see https://help.github.com/articles/page-build-failed-config-file-error.

GitHub Pages was recently upgraded to Jekyll 3.0. It may help to confirm you're using the correct dependencies:

  https://github.com/blog/2100-github-pages-now-faster-and-simpler-with-jekyll-3-0

If you have any questions you can contact us by replying to this email.
{% endraw %}{% endhighlight %}


If tag error:

{% highlight html %}{% raw %}
The page build failed with the following error:

The tag `if` on line 15 in `_includes/head.html,` was not properly closed. For more information, see https://help.github.com/articles/page-build-failed-tag-not-properly-closed.
{% endraw %}{% endhighlight %}



Syntax highlighter error:
{% highlight html %}{% raw %}
The page build completed successfully, but returned the following warning:

You are attempting to use the 'pygments' highlighter, which is currently unsupported on GitHub Pages. Your site will use 'rouge' for highlighting instead. To suppress this warning, change the 'highlighter' value to 'rouge' in your '_config.yml' and ensure the 'pygments' key is unset. For more information, see https://help.github.com/articles/page-build-failed-config-file-error/#fixing-highlighting-errors.

For information on troubleshooting Jekyll see:

  https://help.github.com/articles/troubleshooting-jekyll-builds

If you have any questions you can contact us by replying to this email.
{% endraw %}{% endhighlight %}



Finally the most frustrating error,

Generic Jekyll build failures:

```
The page build failed with the following error:

Page build failed. For more information, see https://help.github.com/articles/troubleshooting-github-pages-build-failures.

For information on troubleshooting Jekyll see:

  https://help.github.com/articles/troubleshooting-jekyll-builds

If you have any questions you can contact us by replying to this email.

```


If the email does not specify the error then you are on your own! This is what I received last time. It doesn't have much information. 


I thought it was because I pushed a new post. But even after removing that post, the error existed. While pushing that article, I also changed few design elements. I changed all of them back to normal, but there was no success.

## Initial check for page build error
 **Step 1:**
 Check if the last post has any markdown syntax error.
 
 **Step2:** 
 If you have made any recent CSS changes then check whether you have any curly braces or semicolons missing.

**Step3:**
If you have edited html or liquid syntax then check whether any tag is missing. Many times we forget to add ``</div>``, ``{% raw %}{% endfor %}{% endraw %}``, ``{% raw %}{% endif %}{% endraw %}``.  Check [this article](https://help.github.com/articles/troubleshooting-jekyll-builds/){: target="_blank" rel="nofollow"} for all kinds of errors possible.

{% include adsense-inside-post-2.html %}

**Step 4:**
Check if a new version of Jekyll is released. Last time when Jekyll 3.0 was released, many jekyll sites using ``realtive_permalink`` got such page build errors because it was deprecated. Even for people using ``highlighter`` other than **rouge** got an error.

If none of these work for you then you should try the next method called exclusion method(or I call it so).

## Exclusion method
Jekyll site is basically divided into **Homepage**, **Pages**, **Posts** and sometimes **Collections**. We exclude one by one in order to check which part is throwing an error. As long as the error goes away, Github will not make any changes to your site.

<div class="warning">
<h3>Backup</h3>
<p>
While performing exclusion method, you may mess up the content of your local repository. It is better to keep a backup of the whole repository in a different location.
</p>
</div>

**Step 1:**
Remove all the content from ``index.html`` or ``index.md`` in the root directory. Push changes to check if you see any error. If no error then you can easily find it inside ``index.html`` file.

**Step :2:** 
Remove all the content from ``page.html`` in **_layouts** folder. Now push the changes to see the errors are solved.

**Step 3:**
Do the same for ``post.html``. If you observe an error then move to step 4. If the error is gone then revert the changes and target ``posts.html``. Now remove ``{% raw %}{{ contents }}{% endraw %}`` from ``post.html`` and push changes. If you get no error then the problem is with posts. You should check individual posts. If you receive an error then posts are alright but something in the post layout is not right.


Do similar process for all the content in your post layout till you get no error and then once you come down to an element which is wrong, see why that is happening.

By using this method I cornered this piece of code causing the problem

{% highlight html %}{% raw %}
<time>{{ page.date | date_to_string }}</time>
{% endraw %}{% endhighlight %}

I'm not sure why the error happened for a code which seems to be valid. But anyway, I changed it to

{% highlight html %}{% raw %}
<time>{{ page.date | date: '%B %d, %Y' }}</time>
{% endraw %}{% endhighlight %}

That solved the error!


## Conclusion
Page build errors are pretty common for beginners. When you get those, you should try to find the root cause. That's how we learn to code better. I wish Github had more targeted ways to find the error and inform its users. That might take long but for now, we have to solve such problems on our own. Also, keep an eye on the latest releases by Jekyll.

If you have any suggestion, then please leave it in the comment section.

Thanks for reading!