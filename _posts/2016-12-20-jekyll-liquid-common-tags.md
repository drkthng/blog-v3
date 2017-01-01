---
title: Most commonly used Jekyll Liquid Tags
desc: Jekyll Liquid tags like Jekyll date, time and variables like site.pages, page.content etc., are some of the most commonly used Jekyll variables. Here is a searchable list for those who are looking for such tags, site and page variables.
author: sharathdt
tags: Jekyll
image: jekyll-frequently-used-variables.png
img-src: "http://www.freepik.com/free-vector/essential-laboratory-objects_849864.htm"
img-src-name: Design by Freepik
layout: post
permalink: /common-jekyll-tags/
---

<style>
.jekyll-es td {
  padding:10px; 
  border:solid 1px #eee;
}
.jekyll-es td:first-child {
    background-color: #2ba06e;
    color: #fff;
    width: 40%;

}

input.search  {
    width: 100%;
    height: 30px;
    padding: 5px 10px;
    border-radius: 5px;
    outline: none;
    border: 1px solid #ddd;
    font-size: 20px;
}
input:focus {
  outline:none;
  border-color:#aaa;
}
.sort {
  padding:8px 30px;
  border-radius: 6px;
  border:none;
  display:inline-block;
  color:#fff;
  text-decoration: none;
  background-color: #28a8e0;
  height:30px;
}
.sort:hover {
  text-decoration: none;
  background-color:#1b8aba;
}
.sort:focus {
  outline:none;
}
.sort:after {
  display:inline-block;
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-bottom: 5px solid transparent;
  content:"";
  position: relative;
  top:-10px;
  right:-5px;
}
.sort.asc:after {
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 5px solid #fff;
  content:"";
  position: relative;
  top:4px;
  right:-5px;
}
.sort.desc:after {
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-bottom: 5px solid #fff;
  content:"";
  position: relative;
  top:-4px;
  right:-5px;
}


.tab-title {
    padding: 15px 0 0 0;
}

</style>

<h1>Search a tag</h1>

<div class="container-list">
    <div id="users">
     
      <input class="search" placeholder="Search" />
      <br />
      <table class="jekyll-es">

        <tbody class="list">
  
        <tr >
            <th class="tab-title">Time Variables</th>
            <th class="tab-title">Output</th>
        </tr>
            
          <tr>
            <td class="variable">{% raw %}{{site.time}}{% endraw %}</td>
            <td class="output">{{site.time}}</td>
          </tr>
                  
          <tr>
            <td class="variable">{% raw %}{{site.time | date: '%B %d, %Y'}}{% endraw %}</td>
            <td class="output">{{site.time | date: '%B %d, %Y'}}</td>
          </tr>
                  
          <tr>
            <td class="variable">{% raw %}{{site.time | date_to_string }}{% endraw %}</td>
            <td class="output">{{site.time | date_to_string }}</td>
          </tr>
          
          
                           
          <tr>
            <td class="variable">{% raw %}{{site.time | date_to_long_string }}{% endraw %}</td>
            <td class="output">{{site.time | date_to_long_string }}</td>
          </tr>
          
          
                           
          <tr>
            <td class="variable">{% raw %}{{site.time | date_to_xmlschema}}{% endraw %}</td>
            <td class="output">{{site.time | date_to_xmlschema}}</td>
          </tr>
          
          
                           
          <tr>
            <td class="variable">{% raw %}{{site.time | date_to_rfc822 }}{% endraw %}</td>
            <td class="output">{{site.time | date_to_rfc822 }}</td>
          </tr>
          
          
                           
          <tr>
            <td class="variable">{% raw %}{{site.time| date: "%Y-%m-%d" }}{% endraw %}</td>
            <td class="output">{{site.time| date: "%Y-%m-%d" }}</td>
          </tr>
          
          
                           
          <tr>
            <td class="variable">{% raw %}{{site.time  | date: "%m/%d/%Y" }}{% endraw %}</td>
            <td class="output">{{site.time  | date: "%m/%d/%Y" }}</td>
          </tr>
                    
                           
          <tr>
            <td class="variable">{% raw %}{{site.time | date: "%-m/%-d/%Y"}}{% endraw %}</td>
            <td class="output">{{site.time | date: "%-m/%-d/%Y"}}</td>
          </tr>
                    
                           
          <tr>
            <td class="variable">{% raw %}{{site.time | date: "%A, %B %-d, %Y"}}{% endraw %}</td>
            <td class="output">{{site.time | date: "%A, %B %-d, %Y"}}</td>
          </tr>
             
        <tr >
            <th class="tab-title">Site Variables</th>
            <th class="tab-title">Output</th>
        </tr>
            
          <tr>
            <td class="variable">{% raw %}{{site.pages}}{% endraw %}</td>
            <td class="output">A list of all Pages.</td>
          </tr>
          
         <tr>
            <td class="variable">{% raw %}{{site.posts}}{% endraw %}</td>
            <td class="output">A reverse chronological list of all Posts.</td>
          </tr>
                                      
           <tr>
            <td class="variable">{% raw %}{{site.related_posts}}{% endraw %}</td>
            <td class="output">A list of up to ten related Posts.</td>
          </tr>
                                      
                                  
                                                  
           <tr>
            <td class="variable">{% raw %}{{site.static_files}}{% endraw %}</td>
            <td class="output">A list of all static files.</td>
          </tr>
                                      
                                  
                                                  
           <tr>
            <td class="variable">{% raw %}{{site.html_pages}}{% endraw %}</td>
            <td class="output">A subset of <code>site.pages</code> listing those which end in <code>.html</code>.</td>
          </tr>
                                      
                                  
                                                  
           <tr>
            <td class="variable">{% raw %}{{site.html_files}}{% endraw %}</td>
            <td class="output">A subset of <code>site.static_files</code> listing those which end in <code>.html</code>.</td>
          </tr>
                                      
                                  
                                                                  
           <tr>
            <td class="variable">{% raw %}{{site.data}}{% endraw %}</td>
            <td class="output">A list containing the data loaded from the YAML files located in the _data directory.</td>
          </tr>
                                                                                          
           <tr>
            <td class="variable">{% raw %}{{site.documents}}{% endraw %}</td>
            <td class="output">A list of all the documents in every collection.</td>
          </tr>
                                                                                          
           <tr>
            <td class="variable">{% raw %}{{site.collections}}{% endraw %}</td>
            <td class="output">A list of all the collections.</td>
          </tr>
                                                                                          
           <tr>
            <td class="variable">{% raw %}{{site.categories.CATEGORY}}{% endraw %}</td>
            <td class="output">The list of all Posts in category CATEGORY.</td>
          </tr>
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{site.tags.TAG}}{% endraw %}</td>
            <td class="output">The list of all Posts with tag TAG.</td>
          </tr>
                                                                                                              


                                      
<tr >
    <th class="tab-title">Page Variables</th>
    <th class="tab-title">Output</th>
</tr>        
          
                                                                                                                                
           <tr>
            <td class="variable">{% raw %}{{page.content}}{% endraw %}</td>
            <td class="output">The content of the Page.</td>
          </tr>
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.title}}{% endraw %}</td>
            <td class="output">The title of the Page.</td>
          </tr>
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.excerpt}}{% endraw %}</td>
            <td class="output">The un-rendered excerpt of the Page.</td>
          </tr>
                
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.url}}{% endraw %}</td>
            <td class="output">he URL of the Post without the domain, but with a leading slash - {{page.url}}</td>
          </tr>
                
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.id}}{% endraw %}</td>
            <td class="output">An identifier unique to the Post .</td>
          </tr>
                
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.excerpt}}{% endraw %}</td>
            <td class="output">The un-rendered excerpt of the Page.</td>
          </tr>
                
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.categories}}{% endraw %}</td>
            <td class="output">The list of categories to which this post belongs.</td>
          </tr>
                
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.tags}}{% endraw %}</td>
            <td class="output">The list of tags to which this post belongs.</td>
          </tr>
                
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.path}}{% endraw %}</td>
            <td class="output">The path to the raw post or page. Ex: {{page.path}}.</td>
          </tr>
                
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.next}}{% endraw %}</td>
            <td class="output">The next post relative to the position of the current post in <code>site.posts</code></td>
          </tr>
                
                                                                                                              
           <tr>
            <td class="variable">{% raw %}{{page.previous}}{% endraw %}</td>
            <td class="output">The previous post relative to the position of the current post in <code>site.posts</code></td>
          </tr>
                                                                                                                                                                                                                                                                      
           <tr>
            <td class="variable">{% raw %}{{page.excerpt}}{% endraw %}</td>
            <td class="output">The un-rendered excerpt of the Page.</td>
          </tr>
                                                                                                                                                        
                                                                                                                                                                                                                                    
        </tbody>
      </table>




</div>

</div>
<br />
<br />


Source: [https://jekyllrb.com/docs/variables/](https://jekyllrb.com/docs/variables/)

{% include adsense-inside-post.html %}

If you think that any frequently used Jekyll variable is missing then do let me know in the comments.
<script src="/js/list.min.js"></script>
<script>
var options = {
  valueNames: [ 'variable', 'output' ]
};
var userList = new List('users', options);
</script>
