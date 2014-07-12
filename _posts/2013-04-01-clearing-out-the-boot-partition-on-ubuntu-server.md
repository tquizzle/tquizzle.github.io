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
Recently I had an issue where I could no longer update packages. The system was responding normally, but after digging around, I found that the /boot partition was 100% full.

After digging around on Google for a while, I found this little gem.

<pre class="brush: bash; title: ; notranslate" title="">dpkg --get-selections|grep 'linux-image*'|awk '{print $1}'|egrep -v "linux-image-$(uname -r)|linux-image-generic" |while read n;do apt-get -y remove $n;done
</pre>

This finds all the linux-image that are in your /boot partition and one-by-one removes them.

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-11619"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-11619"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/?share=facebook" title="Share on Facebook" id="sharing-facebook-11619"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
        </li>
        <li>
          <a href="#" class="sharing-anchor sd-button share-more"><span>More</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
      
      <div class="sharing-hidden">
        <div class="inner" style="display: none;">
          <ul>
            <li class="share-linkedin">
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-11619"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/clearing-out-the-boot-partition-on-ubuntu-server/" title="Click to print"><span>Print</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-end">
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</div>