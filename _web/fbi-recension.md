---
title: "FBI recension"
date: 2017-11-09 07:01:00 +0100
tags: recension
excerpt: "FBI is the cia installer for excellence."
---
## Description and Usage
FBI is a `.cia` installer. It allows you to install signed and/or **un**signed `.cia`s, depending on whether or not you had run waithax, or you have sighax.

### Features
+ Installs `.cia`s seamlessly

{% capture themenot %}Customize appearance by placing replacements for RomFS resources in "sdmc:/fbi/theme/".{% endcapture %}
<div class="notice--info">{{ themenot | markdownify }}</div>

## My Considerations

### Pros
+ Open-Source
+ You can install `.cia`s with a qr code
+ You can install `.cia`s from <http://titledb.com>
+ The theme is customizable

### Cons
+ If you use a Mac, FBI will try to install the `.[title].cia` file automatically created by the Mac, reporting an error