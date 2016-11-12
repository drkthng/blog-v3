---
title: Night Mode Toggle Across the Website!
desc: Changing background color to dark helps reading under low light. This can be achieved easily using javascript. But here is a way to do it across the website.
author: sharathdt
tags: Web-Design
image: toggle-night-mode.png
layout: post
permalink: "/dark-theme-switch"
---

I'm not proud of using a smartphone to read articles on the bed. But this is a habit that many people have. Reading in low light is bad for your eyes if the phone emits a lot of bright light.

![Dark mode](/images/reading-at-night-on-smartphone-dark-mode.jpg)

There are [apps](https://redgadgets.com/protect-eyes-from-computer/){: target="_blank"} that you can use to reduce the light. A better option is to have a dark theme. Apps like Reddit already has this option. Maybe they know their users are nocturnal!

## How to create a dark mode?
When I thought of this problem, I knew JavaScript can do it but [I'm a noob in JS](https://js.webjeda.com){: target="_blank"}. I don't really create my own script. I copy from some pre-existing script and make changes as I like.

But this seemed very easy and I gave it a try to write something on my own which was a horrible code.

{% highlight html %}

<!DOCTYPE html>
<html lang="en">
<head >
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body style="background-color: rgb(255, 255, 255)">
    <p>The button below will switch background color!</p>
    <button onclick="dark()">Switch color</button>
    
    
    <script>
    function dark() {
        if (document.body.style.backgroundColor == 'rgb(255, 255, 255)') {

                document.body.style.backgroundColor = '#333';
        }
        else {
                document.body.style.backgroundColor = 'rgb(255, 255, 255)';
        }
    }
    </script>
    
</body>
</html>

{% endhighlight %}

Copy the code, save as HTML file and open in a browser to see how this works. It is pretty much like the below box.

<div id="dark-div" style="background-color: rgb(255, 255, 255); padding:30px 60px; border: 1px dashed #000; width: 150px;text-align:center;margin: 10px;cursor: pointer" onclick="dark()">
    <p>Click me</p>
</div>


This one works as expected. But I tell you this wasn't easy. First thing is that the JS recognized only RGB code and not HEX. It took me a while to figure that out. It switches background color inline only. Also if you refresh the browser, background color goes back to default.

## Store value across the domain

The problem with this approach is that it is specific to a page. If you switch the theme to dark and navigate to another page in the same domain then it will go back to its normal light theme.

We want it to remember the last switch and keep it across the domain. So if a user switches the theme once then it should remain switched unless he restarts the browser.

Using cookies is one option but it is so yesterday. Europeans know the headache of using cookies on a website. 

A better way is to use either ``localStorage`` or ``sessionStorage``. HTML5 has these options to store up to 5MB of data until you close the browser(sessionStorage) or clear the cache(localStorage). 

After searching through StackOverflow and MDN, I came up with a working code.


## sessionStorage to switch theme

Here is the same box which switches its color but retains even if you refresh the page! Actually, it refreshes once you click on it.

<div id="dark-div-2" style="background-color: rgb(255, 255, 255); padding:30px 60px; border: 1px dashed #000; width: 150px;text-align:center;margin: 10px;cursor: pointer" onclick="darker()">
    <p>Switch</p>
</div>


This uses sessionStorage to pull that off. If you close the browser and open this link again, you'll see that the box goes back to default background.

I have used this in my new theme [Hagura](http://webjeda.com/hagura/){: target="_blank"}. 

{% include adsense-inside-post.html %}

Here is the code I have used to make this happen.

{% highlight javascript %}
function theme() {
     if ( data === 'rgb(255, 255, 255)') {
         
        sessionStorage.setItem('bg', 'rgb(6, 23, 37)');
        sessionStorage.setItem('cc', '#777');
        document.location.reload();

     }
    else if (data == null || undefined) {
        sessionStorage.setItem('bg', 'rgb(6, 23, 37)');
        sessionStorage.setItem('cc', '#777');
        document.location.reload();
    }
    else if( data === 'rgb(6, 23, 37)') {
        
        sessionStorage.setItem('bg', 'rgb(255, 255, 255)');
        sessionStorage.setItem('cc', '#333');
        document.location.reload();
  
    }

};

var data = sessionStorage.getItem('bg');
var color = sessionStorage.getItem('cc');
document.body.style.backgroundColor = data;
document.body.style.color = color;
{% endhighlight %}

This for me looks way too long to do such a simple job. But as I told before I'm a novice JavaScript coder. I coded it to get the work done. I think it can be improved. 

**1.** It needs to be simple. If you observe the code, there is a lot of repetitive values which can be minimized.

**2.** It should not refresh. The changed color will not apply unless the page is refreshed. This is an inconvenience. I hope this can be solved by someone who knows JS.

Even though the page gets refreshed, it will come back to the same scroll location. Because I'm using ``document.location.reload();``

## Conclusion
Though it isn't perfect yet, I think it can be used to implement theme switching or any other change that is supposed to happen across the website. 

Let me know if you have successfully implemented this on your website.

Thanks for reading!

<script>
function dark(){"rgb(255, 255, 255)"==document.getElementById("dark-div").style.backgroundColor?(document.getElementById("dark-div").style.backgroundColor="#333",document.getElementById("dark-div").style.color="#fff"):(document.getElementById("dark-div").style.backgroundColor="rgb(255, 255, 255)",document.getElementById("dark-div").style.color="#333")};
</script>
<script>
function darker(){"rgb(255, 255, 255)"===data?(sessionStorage.setItem("bg","rgb(51, 51, 51)"),sessionStorage.setItem("cc","#fff"),document.location.reload()):null==data?(sessionStorage.setItem("bg","rgb(51, 51, 51)"),sessionStorage.setItem("cc","#fff"),document.location.reload()):"rgb(51, 51, 51)"===data&&(sessionStorage.setItem("bg","rgb(255, 255, 255)"),sessionStorage.setItem("cc","#333"),document.location.reload())}var data=sessionStorage.getItem("bg"),color=sessionStorage.getItem("cc");
document.getElementById("dark-div-2").style.backgroundColor=data;document.getElementById("dark-div-2").style.color=color;
</script>