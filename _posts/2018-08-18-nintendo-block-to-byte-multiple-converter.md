---
header:
  teaser: https://raw.githubusercontent.com/Samplasion/blockconverter/master/docs/blockconverter-gui.PNG
title: "Let's make: Nintendo block to Megabyte/Gigabyte converter"
date: 2018-08-10 15:50 +0100
tags: game games Nintendo GB MB Block blocks
categories: Nintendo
layout: single
comments: true
excerpt: "In this post we'll make a block converter in Ruby, and try to make a gem for it."
---

To make a block converter, we need to know what the conversions are:

|/\/\/\/\| MB | GB |
|--------|----|----|
| Block | 1 MB = 8 blocks | 1 GB = 8192 blocks |

Then, we can start defining functions:

```rb
def bl_to_mb(bl) # block to mb
  return bl / 8
end

def bl_to_gb(bl) # block to gb
  return bl_to_mb(bl) / 1024 # nesting
end
```
