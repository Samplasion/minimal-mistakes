---
header:
  teaser: http://robohub.org/wp-content/uploads/2016/06/technology-1283624_1280-1024x576.jpg
title: "I was thinking so much to the look&feel and structure of this site, that..."
excerpt: "In this post, I'll repair my forgetfulness and write some code. Yayy!"
date: 2017-11-14 20:32:00 +0100
tags: code
categories: code
layout: single
comments: true
toc: true
---

{% include figure image_path="http://robohub.org/wp-content/uploads/2016/06/technology-1283624_1280-1024x576.jpg" alt="Code" %}
Today I’ve noticed that I haven't created nor linked pages to my (few) projects. So, to repair my forgetfulness, we'll build some simple apps.
{% capture warning %}
**Please notice** that, unless noted, the examples below need a file called _script.js_, with the scripts, in the same folder as _index.html_.
{% endcapture %}
<div class="notice notice--warning">{{ warning | markdownify }}</div>
{% capture warnin %}
**Please notice**: I’ll try to make all IDs of the pieces of code unique. In case there are two or more same IDs, there will be a warning `<div>`, and you’ll need to edit parts of the code by yourself.
{% endcapture %}
<div class="notice notice--warning">{{ warnin | markdownify }}</div>

## A Copyright Generator App
### HTML
<pre>{% highlight html %}
<input oninput="genCopy(this.value, 'result')" onchange="genCopy(this.value, 'result')">
<div id="result"></div>
<script src="script.js"></script>
{% endhighlight %}</pre>
### JS
{% highlight js %}
function genCopy(string, id) {
  document.getElementById(id).innerHTML = `Copyright © 2017 ${string}. All Rights Reserved.`
}
{% endhighlight %}
### Result
<input oninput="genCopy(this.value, 'resul')" onchange="genCopy(this.value, 'resul')">
<div id="resul"></div>
<script>
function genCopy(string, id) {
  document.getElementById(id).innerHTML = `Copyright © 2017 ${string}. All Rights Reserved.`
}</script>

## A Random Number Generator
### HTML
<pre>{% highlight html %}
<button onclick="genNum('random')">Generate Number</button>
<!--<p>The number is:</p>--><span id="random"></span>
<script src="script.js"></script>
{% endhighlight %}</pre>
### JS
{% highlight js %}
function genNum(id) {
  var nRand = Math.floor((Math.random() * 1000) + 1);
  document.getElementById(id).innerHTML = nRand;
}
{% endhighlight %}
### Result
<button onclick="genNum('random')">Generate Number</button>
<!--<p>The number is:</p>--><span id="random"></span>
<script>
function genNum(id) {
  var nRand = Math.floor((Math.random() * 1000) + 1);
  document.getElementById(id).innerHTML = nRand;
}
</script>
