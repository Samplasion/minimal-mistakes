---
header:
  teaser: https://raw.githubusercontent.com/Samplasion/blockconverter/master/docs/blockconverter-gui.PNG
title: "Let's make: Nintendo block to Megabyte/Gigabyte converter"
date: 2018-08-18 10:20 +0100
tags: game games Nintendo GB MB Block blocks
categories: Nintendo
layout: single
comments: true
excerpt: "In this post we'll make a block converter in Ruby."
---

To make a block converter, we need to know what the conversions are:

|/\\/\\/\\/\\| MB | GB |
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

def mb_to_bl(mb)
  return mb * 8
end

def gb_to_bl(gb)
  return gb * 8192
end

# we’ll include mb -> gb and viceversa for the sake of completion
def mb_to_gb(mb)
  return mb / 1024
end

def gb_to_mb(gb)
  return gb * 1024
end
```
