---
header:
  teaser: https://eladnava.com/content/images/2016/05/npm-1.jpg
title: "How to install NPM modules on Glitch"
date: 2018-10-15 15:38:00 +0200
tags: tutorial bot js javascript glitch
categories: Tutorials
layout: single
comments: true
excerpt: "A quick tutorial on how to install NPM modules on Glitch"
---

Some days ago I was helping a friend hosting his project on [Glitch](https://glitch.com). The question is, every time he wanted to add a module to his project, he would ask me to do so (not that it was a hassle for me).
So, if you're here, it means you're asking the same question and, ladies and gentlemen, you found the right spot!

Alright, what you need to do is this:
 * Go in your project's `package.json`
 * Click the "Add Package" button up in the code <br>
 ![The button](/assets/images/glitch_add_package.png)
 * Now input the name of the module you want to install. The options are two:
   * Glitch can find the module. Click on its name and reboot the project.
   * Glitch can _not_ find the module. Unfortunately, Glitch doesn't update its package search very often. In this case, manually add an entry in the `package.json`.
 * Profit!
 
If for some reason you can't do something reported here, ask in the comments and I'll reply ASAP.
