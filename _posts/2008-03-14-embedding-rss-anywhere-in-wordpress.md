---
title: Embedding RSS Anywhere in WordPress
author: TQuizzle
layout: post
permalink: http://bit.ly/11zMsbT
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
  - http://bit.ly/11zMsbT
bitly_hash:
  - 11zMsbT
bitly_long_url:
  - http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/
categories:
  - Normal
tags:
  - code
  - feeds
  - php
  - RSS
  - WordPress
---
For some reason or another, I never figured out until today digging through the widgets files in *wp-includes* directory in your default WordPress installation, that you could easily insert RSS feeds anywhere in your site.

This started with a task I had for <a rel="nofollow" target="_blank" href="http://www.makeuseof.com">MakeUseOf.com</a> to include RSS feeds for the author pages. After digging into it, I found it was quite easy and it uses the Magpierss code almost exactly.

All you really have to do is insert a little code in the template file you want to use (or a page or post using one of many php inclusion plugins for WordPress).  
<!--more-->

  
Insert this into the top of the file, post or page as it sets up the RSS parser:

`<?php&#160; /* WP RSS Reader Includes */<br />
&#160;&#160;&#160; require_once(ABSPATH . WPINC . '/rss.php');<br />
 ?>`

Then to include the feed:

`<?php<br />
&#160;&#160; $num_items = 10;&#160; <br />&#160;&#160; $url = <a rel="nofollow" target="_blank" href="http://feed_url_you_want">http://feed_url_you_want</a>;   <br />&#160;&#160; $rss = @fetch_rss( $url );    <br />&#160;&#160; $items = array_slice($rss->items, 0, $num_items);  <br />&#160;&#160;echo "<br />\n<h4>" . $rss->channel['title'] . "</h4>";    <br />&#160;&#160; echo "<dl class=\"thepost\">\n";    <br />&#160;&#160; foreach ($items as $item) {    <br />&#160;&#160;&#160;&#160;&#160;&#160; $href = $item['link'];    <br />&#160;&#160;&#160;&#160;&#160;&#160; $title = $item['title'];    <br />&#160;&#160;&#160;&#160;&#160;&#160; echo "<dt><a href=$href>$title</a></dt>\n";    <br />&#160;&#160; }    <br />&#160;&#160; echo "</dl>";&#160;&#160;&#160;&#160;&#160;&#160;&#160; <br />&#160;&#160; ?>`

Here I use the "array_slice" to only grab a set number of items and&#160; a definition list to display them, you could just as easily substitute this to use an unordered list. I also only grab the headlines. You could just include the description of the feed by adding the variable `$desc = $item['description'];` in the foreach loop.

If you&#8217;d like to be nice to your webserver, setup a magpierss cache directory. Create a directory on your server that has chmod 777 privileges and define it after you setup the RSS parser.  
Simply add this:

`	define('MAGPIE_CACHE_DIR', ABSPATH . '/path_to_your_cache_directory'); `

There you go, you now can easily pump feeds inside anywhere in WordPress.

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-108"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-108"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/?share=facebook" title="Share on Facebook" id="sharing-facebook-108"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-108"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/embedding-rss-anywhere-in-wordpress/" title="Click to print"><span>Print</span></a>
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