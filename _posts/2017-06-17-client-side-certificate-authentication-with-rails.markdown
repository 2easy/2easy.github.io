---
layout: post
title:  "Client Side Certificate Authentication with Ruby on Rails"
date:   2017-06-17 20:29:36 +0200
categories: rubyonrails security
---
This article will be about client side certificate authentication - a concept propably foreign to average RoR developer. This method of authenticating users is used internally in big corporations, where security is top priority. Because some of you migth not be fammiliar with this concept allow me to make a brief introduction.

{% highlight nginx %}

server {
    listen 80;
    listen 443 ssl;
    ssl    on;

    server_name yoursite.xyz;

    ssl_certificate /etc/nginx/certs/server.crt;
    ssl_certificate_key /etc/nginx/certs/server.key;
    ssl_client_certificate /etc/nginx/certs/ca.crt;
    ssl_verify_client optional;

    location / {
        proxy_set_header X-Real-IP  $remote_addr;
        proxy_set_header X-FORWARDED_PROTO https;
        proxy_set_header X-SSL-Client-S-DN   $ssl_client_cert;
        proxy_set_header X-CLIENT-VERIFY $ssl_client_verify;

        proxy_pass http://127.0.0.1:2017;
    }
}

{% endhighlight %}

Check out more about client side certificates [here][wiki-cert].

[wiki-cert]: http://publib.boulder.ibm.com/tividd/td/ITAME/SC32-1359-00/en_US/HTML/am51_webseal_guide58.htm 
