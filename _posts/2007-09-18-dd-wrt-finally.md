---
title: DD-WRT Finally
author: TQuizzle
layout: post
permalink: http://bit.ly/12K7UlW
pdrp_attributionLocation:
  - end
image:
  - 
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
  - http://bit.ly/12K7UlW
bitly_hash:
  - 12K7UlW
bitly_long_url:
  - http://www.tquizzle.com/archive/dd-wrt-finally/
categories:
  - Normal
tags:
  - DD-WRT
  - firmware
  - LifeHacker
  - Linksys
  - Linux
  - router
  - VxWorks
  - wireless
---
<div class="mceTemp">
</div>

<div style="width: 310px" class="wp-caption alignright">
  <a rel="nofollow" target="_blank" href="http://i2.wp.com/commons.wikipedia.org/wiki/File:Linksys-Wireless-G-Router.jpg" target="_blank"><img class="zemanta-img-inserted zemanta-img-configured" title="English: A Linksys wireless-G router." src="http://i2.wp.com/upload.wikimedia.org/wikipedia/commons/thumb/3/34/Linksys-Wireless-G-Router.jpg/300px-Linksys-Wireless-G-Router.jpg?resize=300%2C257" alt="English: A Linksys wireless-G router." data-recalc-dims="1" /></a><p class="wp-caption-text">
    English: A Linksys wireless-G router. (Photo credit: Wikipedia)
  </p>
</div>

For some time, I&#8217;ve thought of pimping out the Linksys <a rel="nofollow" target="_blank" title="My Router" href="http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper">router I have</a>. It&#8217;s been one of the many things I was going to do&#8230;

I had Del.icio.us&#8217;d Adam Pash&#8217;s <a rel="nofollow" target="_blank" href="http://lifehacker.com/software/router/hack-attack-turn-your-60-router-into-a-600-router-178132.php">wonderful Lifehacker article </a>on how to hack your router with Linux, but with all the notices and warnings of the potential to permanently trash your router, I was a bit reluctant to even start this project. Alas I pressed on and am truly happy that I&#8217;d done so.

Adam&#8217;s article was a great starting point, but the model he used was slightly different from mine.&nbsp; The more reading I did, the more I realized that&nbsp;I have to get this right the first time.

<!--more-->

For me, the process went down like this:

1.  Read every possible article referencing the DD-WRT firmware and my router&#8217;s model number.
2.  Crossed my fingers (both hands)
3.  Reset the router to factory defaults, after writing down all the configuration of course
4.  Assigned my laptop a static IP (very important)
5.  Flashed the firmware
*   I actually had to do this a few times.&nbsp;Mine required two&nbsp;initial flashes of <a rel="nofollow" target="_blank" href="http://www.bitsum.com/openwiking/owbase/ow.asp?VxWorks">VxWorks</a>&nbsp;to get things going. <a rel="nofollow" target="_blank" href="http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5%5FCFE">Tutorial Here.</a>

6.  Used tFTP to push the final package (<a rel="nofollow" target="_blank" href="http://www.dd-wrt.com/dd-wrtv2/ddwrt.php">DD-WRT</a>)&nbsp;to the router.
7.  Rejoiced

The first thing I did is exactly what Adam recommended&#8230; boost the wireless signal.&nbsp; Now the DD-WRT gives you the ability to set the wireless transmit power all the way to a maximum of 251 mW from a default of 28 mW.&nbsp; This is definitely way overkill.&nbsp; I set mine to 70, a safe setting according to the DD-WRT manual.&nbsp; At a little more than double the default, 70 mW provides adequate coverage quite a bit more so than before.

It&#8217;s got a plethora of options, settings, abilities that the normal web GUI on the router by default doesn&#8217;t.

Resource Links:

*   <a rel="nofollow" target="_blank" href="http://lifehacker.com/software/router/hack-attack-turn-your-60-router-into-a-600-router-178132.php">Hack Attack: Turn your $60 router into a $600 router &#8211; Lifehacker</a>
*   <a rel="nofollow" target="_blank" href="http://www.dd-wrt.com/wiki/index.php?title=Installation">Installation &#8211; DD-WRT Wiki</a>
*   <a rel="nofollow" target="_blank" href="http://www.dd-wrt.com/wiki/index.php/Supported_Devices">Supported Devices &#8211; DD-WRT Wiki</a>
*   <a rel="nofollow" target="_blank" href="http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5_CFE">Bitsum Technologies Wiki &#8211; WRT54G5 CFE</a>
*   <a rel="nofollow" target="_blank" href="http://www.scorpiontek.org/portal/index.php?option=com_content&task=view&id=27&Itemid=36&limit=modules&limitstart=mod_shoutbox.php?jalGetChat=yes&jal_lastID=97&rand=327195&mosmsg=Thanks+for+your+vote%21">Scorpiontek &#8211; Install DD-WRT</a>

<div class="zemanta-pixie" style="margin-top: 10px; height: 15px;">
  <img class="zemanta-pixie-img" style="border: none; float: right;" src="http://i1.wp.com/img.zemanta.com/pixy.gif" alt="" data-recalc-dims="1" />
</div>

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-69"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-69"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/?share=facebook" title="Share on Facebook" id="sharing-facebook-69"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-69"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/dd-wrt-finally/" title="Click to print"><span>Print</span></a>
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