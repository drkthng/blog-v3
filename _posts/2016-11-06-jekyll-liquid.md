---
title: How to use Liquid Syntax in Jekyll?
desc: Liquid is an open-source templating language. Jekyll makes the best use of Liquid to implement conditional logics, outputs and filters. It may look weird for first timers but it is one of the reasons I'm still using Jekyll. I have discussed how to use Liquid in Jekyll.
author: sharathdt
tags: Jekyll
image: jekyll-liquid.png
img-src: "http://www.freepik.com/free-vector/flowing-down-paint_765063.htm"
img-src-name: Design by Freepik
layout: post
permalink: "/jekyll-liquid/"
---

Liquid Syntax is an open-source template language created by Shopify. Jekyll uses it to load data dynamically, access data across the site, implement conditional logics like **if**, **for**, **case** etc.,

For a beginner, this might look like an alien programming which doesn't resemble any of the programming languages that he/she may have seen before.

* Do not remove this line (it will not be displayed) 
{:toc}

But I assure you that it is probably the simplest and comprehensive language that I have seen so far. Take this snippet for example,

{% highlight liquid %}{% raw %}
{% if age >= 18 %}
  You're allowed to drink beer!
{% else %}
  You are a minor!
{% endif %}
{% endraw %}{% endhighlight %}

So simple isn't it. I wish other programs were also this easy and did not make a fuss whenever I miss a semicolon.

Let's begin learning Liquid keeping Jekyll in mind. There are 3 things that we should know before we jump right in.

| Tags   |      Objects      |  Filters |
|----------|:-------------:|------:|
| {% raw %}{%&nbsp;%}{% endraw %} |  {% raw %}{{ }}{% endraw %} | {% raw %}{{ &nbsp;&#124; }}{% endraw %} |
|Conditions|Output|Modify Output|

### Tags

Tags are functional. They usually tell what to do and how to do something. They are used to implement control flows, iterations etc., The best example for this would be the one I have mentioned above - **legal age for drinking beer**.


Along with conditional statements, tags are also used for special purposes like including a file from ``_includes`` folders. I have also discussed it [here](https://blog.webjeda.com/jekyll-guide/#folders-inside-a-jekyll-site){: target="_blank"}.

{% highlight liquid %}{% raw %}
{% include head.html %}
{% include header.html %}
{% include footer.html %}
{% endraw %}{% endhighlight %}

These statements will look for the files ``head.html``, ``header.html`` and ``footer.html`` and insert them in the places where the tags are defined. I have discussed this here as well.

<p class="r">
Liquid tags and objects will not work on a page if you have not defined front matter in it. At least blank front matter like this <br>
---   <br>
---
</p>

### Objects
Objects are used to output dynamic data on a page. In Jekyll, we have front matter ``title`` for almost all pages and posts. This can be accessed inside that page or post using the following object,


{% highlight liquid %}{% raw %}
{{page.title}}
{% endraw %}{% endhighlight %}

Here is the output of the same object for this page.
{% highlight liquid %}
{{page.title}}
{% endhighlight %}

### Filters 
Filters are used to modify outputs. It is used along with objects. A simple example is shown below.


{% highlight liquid %}{% raw %}
{{page.title | upcase }}
{% endraw %}{% endhighlight %}

Here is the output for this post
{% highlight liquid %}
{{page.title | upcase }}
{% endhighlight %}

Here the output string will be converted into uppercase letters.

I hope by now you have a basic idea of how liquid syntax works. But these are very simple examples. There can be complex liquid code blocks as well. Let's discuss some variables that we can use in Jekyll.

Here is a link for all the filters that you can use: [Liquid Filters](https://help.shopify.com/themes/liquid/filters){: target="_blank"}

## Site Variables
These are sitewide objects. They can be used anywhere on the website to fetch data either something related to the site or data from ``_config.yml`` file.

Some examples here.

| Variable |   Description |
|----------|---------------|
|{% raw %}{{ site.time }}{% endraw %}|Fetches current time - Ex: {{site.time}}|
|{% raw %}{{ site.pages }}{% endraw %}|Fetches a list of all the pages|
|{% raw %}{{ site.posts }}{% endraw %}|Fetches a list of all the posts|
|{% raw %}{{ site.data }}{% endraw %}|Fetches a list containing the data loaded from the YAML files located in the _data directory|

Site variables defined in ``_config.yml`` are very useful and can be used to change things globally. Imagine you define your facebook username in the configuration file. You can access this from anywhere on the site. 

Let's say this is how you define all the social media accounts in ``_config.yml``,
{% highlight yaml %}{% raw %}
facebook: webjeda
twitter: webjeda
github: sharu725
{% endraw %}{% endhighlight %}

Let's say you create an author section with follow buttons,

{% highlight html %}{% raw %}
Follow me on: 
  <a href="https://facebook.com/{{site.facebook}}" target="_blank" >
      <i class="footer-icon fa fa-facebook-official"></i>
  </a>
  
  <a href="https://twitter.com/{{site.twitter}}" target="_blank" >
      <i class="footer-icon fa fa-twitter"></i>
  </a>
  
  <a href="https://github.com/{{site.github}}" target="_blank" >
      <i class="footer-icon fa fa-github-alt"></i>
  </a>
{% endraw %}{% endhighlight %}

Output will look like this

Follow me on: 
  <a href="{{site.facebook}}" target="_blank" >
      <i class="icon fa fa-facebook-official"></i>
  </a>
  <a href="{{site.twitter}}" target="_blank" >
      <i class="icon fa fa-twitter"></i>
  </a>
  <a href="{{site.github}}" target="_blank" >
      <i class="icon fa fa-github-alt"></i>
  </a>
<style>i.icon {margin-left: 10px;}</style>



This comes in very handy if you want to use these variables very often or change them altogether. I have used this feature while creating themes. Defining accent colors in configuration helps change the color globally.


## Page variables

| Variable |   Description |
|----------|---------------|
|{% raw %}{{ page.title }}{% endraw %}|Fetches title of the page. Ex: - {{page.title}}|
|{% raw %}{{ page.content }}{% endraw %}|Fetches anything after frontmatter of the page|
|{% raw %}{{ page.excerpt }}{% endraw %}|Fetches the excerpt or first paragraph of the page|
|{% raw %}{{ page.url }}{% endraw %}|Fetches the url of the page. Ex: for this page - {{page.url}}|

Page variables are page specific. They can only fetch data with respect to the page they are declared in.


## Usage
These variables are very easy to implement but using them within a loop is a little tricky. I will give you some examples,

### For Loop

{% highlight liquid %}{% raw %}
{% for pot in site.posts %}
{{pot.title}}
{% endfor %}
{% endraw %}{% endhighlight %}

The output is here
{% highlight liquid %}
{% for pot in site.posts limit: 3 %}
{{pot.title}}
{% endfor %}
{% endhighlight %}

I'm limiting the outputs to 3. If not, the whole page will be filled with titles. Here, ``pot`` is just a variable. We generally use ``post`` in its place. You can use any word that you fancy.

You can also fetch titles manually (not recommended!)

{% highlight liquid %}{% raw %}
{{ site.posts[0].title }}
{{ site.posts[1].title }}
{{ site.posts[2].title }}
.
.
.
{{ site.posts[n].title }}
{% endraw %}{% endhighlight %}

Here ``n`` should be an integer. This method is not practical. You can use it if you're willing to fetch the titles of first few posts.

For numbering a loop, you can use ``forloop.index``. This can also be used to provide different ids for consecutive elements in a for loop.

{% highlight liquid %}{% raw %}
{% for pot in site.posts %}
{{forloop.index}}. {{pot.title}}
{% endfor %}
{% endraw %}{% endhighlight %}

The output looks like this,

{% highlight liquid %}
1. How to use Liquid Syntax in Jekyll!

2. 14 Ways to Customize your Company Website

3. Jekyll's got a new GUI for local editing!
.
.
.
n. Nth post title
{% endhighlight %}

### If else condition

{% highlight liquid %}{% raw %}
{% if page.title contains 'Jekyll' %}
  This is a Jekyll related article.
{% endif %}

{% if page.title contains 'Liquid' %}
  This is a Liquid related article.
{% endif %}

{% if page.title contains 'Jekyll' and 'Liquid' %}
  This is a Jekyll Liquid article!
{% else %}
  This is neither Jekyll nor a Liquid article.
{% endif %}
{% endraw %}{% endhighlight %}

The output is here
{% highlight liquid %}
{% if page.title contains 'Jekyll' %}
  This is a Jekyll related article.
{% endif %}

{% if page.title contains 'Liquid' %}
  This is a Liquid related article.
{% endif %}

{% if page.title contains 'Jekyll' and 'Liquid' %}
  This is a Jekyll Liquid article!
{% else %}
  This is neither Jekyll nor a Liquid article.
{% endif %}
{% endhighlight %}

Since this page has a title that contains both Jekyll and Liquid, the output is as shown above.

Else if in Jekyll Liquid Syntax is implemented this way,

{% highlight liquid %}{% raw %}
{% if page.url == '/liquid/' %}
  The page URL for this page is /liquid/
{% elsif page.url == '/jekyll-liquid/' %}
  The page URL for this page is /jekyll-liquid/
{% endif %}
{% endraw %}{% endhighlight %}

The output will be,
{% highlight liquid %}
{% if page.url == '/liquid/' %}
  The page URL for this page is /liquid/
{% elsif page.url == '/jekyll-liquid/' %}
  The page URL for this page is /jekyll-liquid/
{% endif %}
{% endhighlight %}

This is exactly how I have implemented active menu highlight for this blog. Navigate to **About** or **Contact** page and see how the colored-underline gets highlighted.

``For loops`` will usually have more than one output but ``if conditions`` will have only one output.
{: .g}

Please go through this [document](https://help.shopify.com/themes/liquid/tags/control-flow-tags){: target="_blank"} to get familiar with other types of condtional flows.

## Also refer:

Liquid: [https://help.shopify.com/themes/liquid](https://help.shopify.com/themes/liquid)

Front Matter: [http://jekyllrb.com/docs/frontmatter/](http://jekyllrb.com/docs/frontmatter/)

Templates: [http://jekyllrb.com/docs/templates/](http://jekyllrb.com/docs/templates/)

{% include table.html %}
