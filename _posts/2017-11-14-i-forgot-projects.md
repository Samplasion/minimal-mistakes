---
header:
  teaser: http://robohub.org/wp-content/uploads/2016/06/technology-1283624_1280-1024x576.jpg
title: "I was thinking so much to the aspect and structure of this site, that..."
excerpt: "In this post, I'll repair for my forgetfulness and write some code. Yayy!"
date: 2017-11-14 20:32:00 +0100
tags: code
categories: code
layout: single
comments: true
toc: true
---

{% include figure image_path="http://robohub.org/wp-content/uploads/2016/06/technology-1283624_1280-1024x576.jpg" alt="Code" %}
Today I noticed that I haven't created nor linked to my (few) projects. So, to repair my forgetfulness, we'll build some simple apps.

### A Copyright Generator App
#### HTML
<pre>{% highlight html %}
<input oninput="genCopy(this.value, 'result')" onchange="genCopy(this.value, 'result')">
<div id="result"></div>
<script src="script.js"></script>
{% endhighlight %}</pre>
#### JS
{% highlight js %}
function genCopy(string, id) {
  document.getElementById(id).innerHTML = `Copyright © 2017 ${string}. All Rights Reserved.`
}
{% endhighlight %}
#### Result
<input oninput="genCopy(this.value, 'resul')" onchange="genCopy(this.value, 'resul')">
<div id="resul"></div>
<script>
function genCopy(string, id) {
  document.getElementById(id).innerHTML = `Copyright © 2017 ${string}. All Rights Reserved.`
}</script>