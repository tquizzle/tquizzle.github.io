---
title: Previous Post / Next Post Image Thumbnails using Autofocus
author: TQuizzle
layout: post
permalink: /archive/previous-post-next-post-image-thumbnails/
image:
  - 
pdrp_attributionLocation:
  - end
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
  - http://bit.ly/12KbLiK
bitly_hash:
  - 12KbLiK
bitly_long_url:
  - http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/
categories:
  - Normal
tags:
  - Autofocus
  - code
  - Feedback
  - Next Post
  - PhotoBlog
  - Photos
  - php
  - Previous Post
  - Thumbnails
  - WordPress
---
So I&#8217;ve been uploading photos for a few months now to my photoblog and it&#8217;s been interesting. I love the Autofocus theme and all the amazing things it does, but it lacked something&#8230;.

### What&#8217;s Missing

My <a rel="nofollow" target="_blank" href="http://photos.tquizzle.com/">photoblog</a>, that is using the amazing <a rel="nofollow" target="_blank" href="http://www.allancole.com/wordpress/themes/autofocus">Autofocus</a> theme is simply that&#8230;a simple photoblog of some of my photos taken from any and everywhere.

I noticed something wasn&#8217;t right and I had one gripe about it&#8230;on single pages it lacked a bit of class and touch that I think photoblogs should have. Mainly I was looking for a previous/next thumbnail support when it displayed previous and next navigation links under the content. I thought that would be a perfect place to put these little gems.

By default, Autofocus theme puts the navigation to the previous and next posts underneath your content photo. Makes perfect sense, but I figured it&#8217;s a friggin photo blog, why not display the previous/next available photo too?  
<!--more-->

  
<img src="http://i2.wp.com/www.tquizzle.com/uploads/2009/11/Picture-3.png?fit=505%2C152" alt="Boring Previous/Next" title="Boring Previous/Next" class="aligncenter size-full wp-image-418" data-recalc-dims="1" />

### Modifications

So tonight, I played with the Autofocus code a bit and produced what I had wanted.

*   Now when you go to an individual image page, you&#8217;ll see all the pertinent information about that photo, but underneath where the preview of the previous and next posts are, you&#8217;ll see those post&#8217;s thumbnail too.
*   The image shown is the thumbnail size setting which is 150X150 of the photo.
*   The previous post&#8217;s image auto floats left while the next post&#8217;s image floats to the right.

That&#8217;s about it, check it out on my <a rel="nofollow" target="_blank" href="http://photos.tquizzle.com">photoblog</a> and please give me some <a rel="nofollow" target="_blank" href="/contact/">feedback</a> or [comment love][1]. Might make that into a little plugin or something.

### Screenshot

<img src="http://i1.wp.com/www.tquizzle.com/uploads/2009/11/Picture-2.png?fit=504%2C763" alt="Zoomed Way Out to see the whole page" title="Zoomed Way Out to see the whole page" class="aligncenter size-full wp-image-415" data-recalc-dims="1" />  
There, now doesn&#8217;t that look better?

### Code Snippet

In the spirit of sharing, I&#8217;ll just go ahead and list the code snippet I used in the &#8220;*single.php*&#8221; in the Autofocus theme folder. Please note, this is just the navigation section below the current post.

<pre class="brush: php; collapse: false; title: ; toolbar: false; wrap-lines: false; notranslate" title="">$previouspost = get_previous_post($in_same_cat, $excluded_categories);

if ($previouspost != null) {
  echo '&lt;div class="nav-previous"&gt;';
  previous_post_link('%link &laquo; Previous');
  echo '&lt;div class="nav-excerpt"&gt;&lt;p&gt;';

  /* Show previous Post's Thumbnail */
  $tq_previouspost_img = get_post_meta($previouspost-&gt;ID, "image_url", $single = true);
  $tq_previouspost_title = get_post($previouspost-&gt;ID);
  $tq_previouspost_title = $tq_previouspost_title-&gt;post_title;
  echo '&lt;img class="alignleft size-thumbnail" src="' . $tq_previouspost_img . '" alt="' . $tq_previouspost_title . '" width="150" height="150" /&gt;';
  /* End previous thumbnail */			

  previous_post_excerpt();
  echo '&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;';
} 

$nextpost = get_next_post($in_same_cat, $excluded_categories);

if ($nextpost != null) {
echo '&lt;div class="nav-next"&gt;';
next_post_link('Next &raquo; %link');
echo '&lt;div class="nav-excerpt"&gt;&lt;p&gt;';

/* Show Next Post's Thumbnail */
$tq_nextpost_img = get_post_meta($nextpost-&gt;ID, "image_url", $single = true);
$tq_nextpost_title = get_post($nextpost-&gt;ID);
$tq_nextpost_title = $tq_nextpost_title-&gt;post_title;
echo '&lt;img class="alignright size-thumbnail" src="' . $tq_nextpost_img . '" alt="' . $tq_nextpost_title . '" width="150" height="150" /&gt;';
/* End Next thumbnail */			

next_post_excerpt();
echo '&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;';
} 
</pre>

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-411"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-411"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/?share=facebook" title="Share on Facebook" id="sharing-facebook-411"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-411"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/" title="Click to print"><span>Print</span></a>
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

 [1]: http://www.tquizzle.com/2009/11/21/previous-post-next-post-image-thumbnails/#respond