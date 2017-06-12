---
layout: post
title: "Hello World"
categories: test
author: "Mariano Trebino"
meta: "Girona"
---

Hello World Sample


<div class="pagination">  
    <div class="prev" align=left>
      {% if page.previous.url %}  
        <a class="prev" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>  
      {% endif %}  
     </div>
    <div class="prev" align=right>
      {% if page.next.url %}  
        <a class="next" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>  
      {% endif %}  
    </div>
</div>  