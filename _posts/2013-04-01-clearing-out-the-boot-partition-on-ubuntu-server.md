---
title: Clearing out the /boot partition on Ubuntu Server
author: TQuizzle
layout: post
permalink: /archive/clearing-out-the-boot-partition-on-ubuntu-server/
pdrp_attributionLocation:
  - caption
image:
  - http://www.tquizzle.com/uploads/2013/04/Boot-Partition-Full-300x268.png
quote-author:
  - Unknown
quote-url:
  - http://
quote-copy:
  - Unknown
audio:
  - http://
link-url:
  - http://
bitly_url:
  - http://bit.ly/12K6Iil
bitly_hash:
  - 12K6Iil
bitly_long_url:
  - http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/
categories:
  - Normal
tags:
  - Linux
  - Ubuntu
---
![Boot Partition Full](http://www.tquizzle.com/uploads/2013/04/Boot-Partition-Full-300x268.png)

Recently I had an issue where I could no longer update packages. The system was responding normally, but after digging around, I found that the /boot partition was 100% full.

After digging around on Google for a while, I found this little gem.

<script src="https://gist.github.com/tquizzle/d5d3ecdab4f251347c01.js"></script>

This finds all the linux-image that are in your /boot partition and one-by-one removes them.
