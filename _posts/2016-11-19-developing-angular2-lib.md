---
layout: post
title: "Developing angular2 lib for ionic"
description: "Problems found while developing an angular2 lib for ionic2"
tags: [angular2, ionic2, npm]
---

Recently I've started creating a library with some ionic and angular classes to be used for different ionic2 apps.
It's been difficult for several reasons. One of them is the following:

#### Don't use npm-link:

I had my library developed and I just had to use it from my ionic2 app.
My main module looked like this:

{% include image.html path="20161119/module.png" path-detail="20161119/module.png" alt="Angular2 module definition" %}

I was following the documentation but I kept getting this error: 
{% include image.html path="20161119/consoleError.png" path-detail="20161119/consoleError.png" alt="Console error" %}

My package json was this one:
{% include image.html path="20161119/packageJson.png" path-detail="20161119/packageJson.png" alt="package Json" %}

##### Solution

My ionic2 lib was called alphacore and before publishing it I was using [npm link](https://docs.npmjs.com/cli/link) to consume it from my application.
Well, it seems that ionic2 build is not handling properly symlinks. I guess it's ngc (angular compiler).
So the **solution** to that problem was: 

1. Unlink the node_module

{% highlight bash %}
npm unlink alphacore
{% endhighlight %}

2. Install properly my library

{% highlight bash %}
npm install alphacore
{% endhighlight %}

or copy the library directly into the node_modules folder.


It took me a while to find it! Hope this doesn't happen to anyone!

