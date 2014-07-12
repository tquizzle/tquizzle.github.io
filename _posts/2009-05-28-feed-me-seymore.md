---
title: Feed Me Seymore
author: TQuizzle
layout: post
permalink: /archive/feed-me-seymore/
bitly_url:
  - http://bit.ly/17PWiif
bitly_hash:
  - 17PWiif
bitly_long_url:
  - http://www.tquizzle.com/archive/feed-me-seymore/
categories:
  - Normal
tags:
  - Error
  - Feed
  - Validate
---
So I noticed something wrong today&#8230;<a rel="nofollow" target="_blank" href="http://feeds2.feedburner.com/Tquizzlecom">my feed</a>. It was returning an error, and not displaying correctly.

Since I don&#8217;t subscribe to to own feed (I&#8217;m not that vain), I didn&#8217;t see that it wasn&#8217;t displaying. It essentially was blank with an error.

Checking out <a rel="nofollow" target="_blank" href="http://feedvalidator.org">FeedValidator.Org</a>, I saw that it not only wasn&#8217;t validating, it had errors on lines 1 and 2&#8230;which were empty. Empty I said? Good thing FeedValidator is so smart, it knew what I was using (WordPress) to produce the feed then offered <a rel="nofollow" target="_blank" href="http://feedvalidator.org/docs/error/WPBlankLine.html">some suggestions</a> to fixing it.

I guess it&#8217;s a known problem with some plugins and theme files having empty lines after or before their relative opening <?php or closing ?> tags.

So began the journey to find out what was causing this&#8230;

Per FeedValidator&#8217;s recommendation, I checked wp-rss2.php and wp-atom.php both of which were fine. Then checked wp-config to see if the problem was there&#8230;still no love. I checked my theme&#8217;s functions.php file since I use that immensely in customizing the look of this blog but it too didn&#8217;t have any empty lines. Next step&#8230;checking **all** the plugins.

For some reason, I started alphabetically from the bottom and checked WP-Super-Cache. Boom. There&#8217;s the culprit. Right at the end of the file there was a ?> followed by two empty lines. I deleted those, and all-of-the-sudden the feed validated again. W00t.

Now you 30 people or so that subscribe to my feed&#8230;it&#8217;s working again. Thanks for hanging in there.

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-284"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-284"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/?share=facebook" title="Share on Facebook" id="sharing-facebook-284"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-284"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/feed-me-seymore/" title="Click to print"><span>Print</span></a>
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