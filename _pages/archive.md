---
layout: page
title: Archive
desc: Find an archive of all our posts here. Every year I try to write more and more useful content on WebJeda. So this is where you can see what all the things I wrote on every single year!
permalink: /archive/
adallow: 0
---
<!-- 
<section id="archive">
  <h2><i class="fa fa-leanpub fa-2x"></i> Articles from this year</h2>
{% for post in site.posts %}
  {% unless post.next %}

  <ul class="this">
  {% else %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
  {% if year != nyear %}
  </ul>
  <h2>{{ post.date | date: '%Y' }}</h2>

  <ul class="past">
  {% endif %}
  {% endunless %}
 <li class="arch-list"><i class="fa fa-circle-thin"></i>&nbsp;<time>{{ post.date | date:"%d %b" }}</time>&nbsp;&nbsp;<a href="{{ post.url }}">{{ post.title }}</a></li>
 {% endfor %}
  </ul>
</section>
 -->

<!----- New --->
<nav class="pills">
<ul style="margin: 0">
<li style="margin: 0"><p>Sort by: </p></li>
<li class="by-category"><a href="#by-category"><p>Category</p></a></li>
<li class="by-date active"><a href="#by-date"><p>Date</p></a></li>
<li class="by-title"><a href="#by-title"><p>Title</p></a></li>
</ul>

</nav>

<div class="by-category hide archive">


<div id="archives">
<h1>Categories</h1>
{% for tag in site.tags %}
  <div class="archive-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
    <div id="#{{ tag_name | slugize }}"></div>
    <a name="{{ tag_name | slugize }}"></a>
    <p></p>
    <h2 class="tag-head">{{ tag_name }}</h2>

    {% for post in site.tags[tag_name] %}
    <article class="archive-item">
      <p style="margin-bottom:10px"><a href="{{ post.url | prepend: site.url }}">{{post.title}}</a></p>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>

</div>


<div class="by-title hide archive">
<h1>Title</h1>
{% assign sorted_pages = (site.posts | sort: 'title') %}
{% for post in sorted_pages %}
<p><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></p>
{% endfor %}
</div>

<div class="by-date archive">
  <section id="archive">
  <h2><i class="fa fa-leanpub fa-2x"></i> Articles from this year</h2>
{% for post in site.posts %}
  {% unless post.next %}
  <ul class="this">
  {% else %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
  {% if year != nyear %}
  </ul>
  <h2>{{ post.date | date: '%Y' }}</h2>

  <ul class="past">
  {% endif %}
  {% endunless %}
 <li class="arch-list"><i class="fa fa-circle-thin"></i>&nbsp;<time>{{ post.date | date:"%d %b" }}</time>&nbsp;&nbsp;<a href="{{ post.url }}">{{ post.title }}</a></li>
 {% endfor %}
  </ul>
</section>

</div>


<script type="text/javascript">
function switch_nav(fragment) {
    var elements = document.querySelectorAll("div.archive");
    for (i = 0; i < elements.length; ++i) {
        elements[i].classList.add("hide");
    }

    elements = document.querySelectorAll("div.archive." + fragment);
    for (i = 0; i < elements.length; ++i) {
        elements[i].classList.remove("hide");
    }
    elements = document.querySelectorAll("nav.pills li");
    for (i = 0; i < elements.length; ++i) {
        elements[i].classList.remove("active");
    }
    elements = document.querySelectorAll("nav.pills li." + fragment);
    for (i = 0; i < elements.length; ++i) {
        elements[i].classList.add("active");
    }
};

document.addEventListener('DOMContentLoaded', function() {

  var fragment = window.location.hash.slice(1);
  if (fragment
      && document.querySelectorAll("div.archive." + fragment).length == 1) {
    switch_nav(fragment);
  };

  var elements = document.querySelectorAll("nav.pills a");
  for (i = 0; i < elements.length; ++i) {
    elements[i].onclick = function(){
      var fragment = this.href.split("#")[1];
      switch_nav(fragment);
      window.location.replace("#" + fragment);
      return false;
    };
  };
});
</script>




