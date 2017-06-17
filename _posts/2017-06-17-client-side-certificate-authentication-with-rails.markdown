---
layout: post
title:  "Client Side Certificate Authentication with Ruby on Rails"
date:   2017-06-17 20:29:36 +0200
categories: rubyonrails security
---
This article will be about client side certificate authentication - a concept foreign to average RoR developer. This method of authenticating users is used internally in big corporations, where security is top priority. Though you might not be aquainted with the concept, let me explain this method first.

{% highlight ruby %}
def generate_cert(name)
  #TODO code
end
generate_cert('tom')
#=> generates certificate for tom
{% endhighlight %}

Check out more about client side certificates [here][wiki-cert].

[wiki-cert]: http://publib.boulder.ibm.com/tividd/td/ITAME/SC32-1359-00/en_US/HTML/am51_webseal_guide58.htm 
