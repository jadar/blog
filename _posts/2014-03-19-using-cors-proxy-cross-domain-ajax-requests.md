---
layout: post
title: Using CORS Proxy for Cross-domain AJAX Requests
---

AJAX requests in Javascript can only be made when being sent to the same domain. This is due to the [same-origin policy](http://en.wikipedia.org/wiki/Same_origin_policy). It is particularly annoying when hosting pages using a service like [GitHub Pages](http://pages.github.com/), and needing to get JSON data that can't be served as [JSON-P](http://json-p.org/). If you could use PHP, you can't on GitHub Pages, you could use a [PHP proxy](http://www.webdevdoor.com/jquery/cross-domain-browser-json-ajax/).  

But for hosting on services like GitHub Pages, you can use [**CORS Proxy**](www.corsproxy.com). All you have to do is strip "http://" and "www." from the URL being proxied, and prepend the URL with ```www.corsproxy.com/```. So ```http://www.jadar.net/``` would be ```http://www.corsproxy.com/jadar.net/```.  
  
Security? Well, CORS Proxy strips any cookie headers. Also, because the domain is ```http://www.corsproxy.com/```, so cookies for the upstream domain aren't sent. You can check the source [here](https://github.com/gr2m/CORS-Proxy).  

Hopefully this has helped you, it stumped me for the longest time before finding CORS Proxy.