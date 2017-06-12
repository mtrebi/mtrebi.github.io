---
layout: post
title: "Hello World"
categories: test
author: "Mariano Trebino"
meta: "Girona"
---

Hello World Sample


<div class="pagination">  
  <div class="next" align="left">
    {% if page.next.url %}  
      <a class="next" href="{{page.next.url}}">&laquo; {{page.next.title}}</a>  
    {% endif %}  
   </div>
  <div class="prev" align="right">
    {% if page.prev.url %}  
      <a class="prev" href="{{page.prev.url}}">{{page.prev.title}} &raquo;</a>  
    {% endif %}  
  </div>
</div>   