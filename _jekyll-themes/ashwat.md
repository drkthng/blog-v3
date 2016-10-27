---
title: Ashwathama
date: 2016-10-27
layout: post
image: ashwat.png
desc: Ashwathama is a minimal website with an app like design. It also features card layouts for website elements.
link: http://ashwathama.s3-website-us-east-1.amazonaws.com/
dlink: 
premium: yes
id: ashwath
---
## Features

### Smartphone App like Layout
The theme is designed keeping smartphones users in mind. An app like design is more comfortable to use on a mobile browser.  

### Minimal & Responsive Card Layout
The theme uses a minimal layout for simplicity. Only the things that matter are shown on the homepage. 

**Images:**

Small images will be shown at their actual size.
![small image]({{page.link}}images/ashwathama-1.jpg)


Large images will always scale down and fit in the content container.
![large image]({{page.link}}images/lost-1.jpg)

**Videos:**

Whenever you add a video, make sure you use the class ``video`` in the iframe or video container. You can also use the shortcode {% raw %}{: .video}{% endraw %} to make the video responsive.

Consider this video for example. If you resize the window to a smaller viewport, the video resizes itself!

<iframe width="854" height="480" src="https://www.youtube.com/embed/YE7VzlLtp-4" frameborder="0" allowfullscreen></iframe>
{: .video}

The code is here
{% highlight html %}
<iframe width="854" height="480" src="https://www.youtube.com/embed/YE7VzlLtp-4" frameborder="0" allowfullscreen></iframe>
{% raw %}{: .video}{% endraw %}
{% endhighlight %}

Take a look at [example post]({{page.link}}example/){: target="blank"} to check responsive nature of other elements.

### 20 Color Schemes!
Customize the theme as you like by using color schemes!

#### Purple

![Purple jekyll theme]({{page.link}}images/Purple.png){: .shadow}

Check [Color Schemes]({{page.link}}color-schemes/){: target="_blank"} for more.


### Search Engine Optimized
The theme is optimized for search engines by default.

### 3 Customizable categories
By default, the theme has 3 categories.

* Design
* Code
* Life

You can always change these to your liking or add extra categories by making little changes in the code.

### Reading Time Estimation
Posts will show an average time required to read the content. 


### Card Themed Author Section
The theme features a card layout theme for author section. It also has social follow buttons.

### Social Share Buttons
Social sharing is kept after every post by default. The code uses only Liquid coding, no js.

### Pre-installed Disqus Comments
Disqus is pre-installed in the theme. You can sign up with Disqus and change the short-name in _config.yml file or leave it blank to not show any comment section. By default, it is left blank.

### Google Analytics
Google analytics is also included in the theme. Just insert UA code in the configuration file. If left blank, the code will not run.

### Clean and Separate CSS
CSS files are separated for easy editing. The theme has separate stylesheets for main elements like header, cards etc.,

### Built-in Contact Form
In the [contact]({{page.link}}contact/){: target="_blank"} page, a contact form is included by default. You can make it work by changing the simpleform-token which can be obtained for free from https://getsimpleform.com/

### Syntax Highlighting
Syntax highlighting is done by rouge. Check [example post]({{page.link}}example/){: target="_blank"}.

### Dynamic RSS Feed
RSS feed is generated dynamically as and when you add posts and pages.


<style>.shadow{
    box-shadow: 2px 2px 5px #aaa;
    border-radius: 0;
}</style>

[**Demo**]({{page.link}}){: .btn }

<form style="width: 100%;border:1px solid #777;padding: 20px;display:inline-block;margin-bottom:1em;" action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
<input type="hidden" name="cmd" value="_s-xclick">
<input type="hidden" name="hosted_button_id" value="6ETS5UPR3XHEJ">
<table>
<tr><td><input type="hidden" name="on0" value="Add ons">Add ons</td></tr><tr><td><select style="border: 1px solid;" name="os0">
	<option value="Just the theme + 3 months support">Just the Theme + 3 Months Support $12.00 USD</option>
	<option value="Initial installation Guide">Initial Installation Guide $18.00 USD</option>
	<option value="Extended 12 months support">Extended 12 Months Support $25.00 USD</option>
</select> </td></tr>
</table>
<input type="hidden" name="currency_code" value="USD">
<input type="image" src="https://www.paypalobjects.com/en_GB/i/btn/btn_buynowCC_LG.gif" border="0" name="submit" alt="PayPal – The safer, easier way to pay online!">
<img alt="" border="0" src="https://www.paypalobjects.com/en_GB/i/scr/pixel.gif" width="1" height="1">
</form>
