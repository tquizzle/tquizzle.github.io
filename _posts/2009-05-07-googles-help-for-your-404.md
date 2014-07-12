---
title: 'Google&#8217;s Help for your 404'
author: TQuizzle
layout: post
permalink: /archive/googles-help-for-your-404/
bitly_url:
  - http://bit.ly/11DTfCr
bitly_hash:
  - 11DTfCr
bitly_long_url:
  - http://www.tquizzle.com/archive/googles-help-for-your-404/
categories:
  - Normal
tags:
  - 404
  - CSS
  - Error
  - Google
  - HTML
  - WordPress
---
So you&#8217;re already ahead of the game by having a good <a rel="nofollow" target="_blank" href="http://www.alistapart.com/articles/perfect404/">404</a> <a rel="nofollow" target="_blank" href="http://www.google.com/support/webmasters/bin/answer.py?answer=93641&#038;hl=en">page</a>, right? Good, now you can even add a bit more spice to them.

While on Google&#8217;s Webmaster Tools page, I noticed this little gem:  
`<script type="text/javascript"><br />
  var GOOG_FIXURL_LANG = 'en';<br />
  var GOOG_FIXURL_SITE = 'http://www.mydomain.com';<br />
</script><br />
<script type="text/javascript" src="http://linkhelp.clients.google.com/tbproxy/lh/wm/fixurl.js"></script>`

Since users need to find what they&#8217;re looking for within 7 seconds to avoid them leaving your site&#8230;use this little guy to help out. It will make it easier for them to find the information they&#8217;re looking for. So, you&#8217;re probably wondering, &#8220;What does that do to help me?&#8221; Good question, here&#8217;s a rundown of what Google says: 
*   It adds a search box for your site with appropriate search suggestions.
*   It tries to provide alternatives to incorrect URLs.

<!--more-->

  
So to make this thing a little more WP friendly, I added the `<?php bloginfo('url'); ?>` to that `GOOG_FIXURL_SITE` variable in the script and shebang, it&#8217;s working like a charm. Now, add it to your 404.php file in your template directory and users might thank you.

Here&#8217;s what it should look like sitting in your 404.php file:  
`<script type="text/javascript"><br />
  var GOOG_FIXURL_LANG = 'en';<br />
  var GOOG_FIXURL_SITE = '<?php bloginfo('url'); ?>';<br />
</script><br />
<script type="text/javascript" src="http://linkhelp.clients.google.com/tbproxy/lh/wm/fixurl.js"></script>`

If you really want to tweak how this gadget looks, <a rel="nofollow" target="_blank" href="http://www.google.com/support/webmasters/bin/answer.py?answer=100044&#038;hl=en">Google&#8217;s provided</a> custom classes that its script uses to give you full customization.

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-261"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-261"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/?share=facebook" title="Share on Facebook" id="sharing-facebook-261"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-261"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/googles-help-for-your-404/" title="Click to print"><span>Print</span></a>
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