---
title: AutoFocus Previous Post / Next Post Image Thumbnails
author: TQuizzle
layout: post
permalink: http://bit.ly/12KdQv3
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
  - http://bit.ly/12KdQv3
bitly_hash:
  - 12KdQv3
bitly_long_url:
  - http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/
categories:
  - Normal
tags:
  - Autofocus
  - code
  - functions
  - Next Post
  - PhotoBlog
  - Previous Post
  - theme
  - Thumbnails
  - TimThumb
  - wordp
---
For a primer, you should check out my [previous post][1] on this topic. There will be some referencing it in this post.

It&#8217;s been a couple of years since that post and many things have changed.  
The theme <a rel="nofollow" target="_blank" href="http://fthrwght.com/autofocus/">AutoFocus</a> has gone through a number of changes. Alan has released a &#8220;Pro&#8221; (paid) version of the theme with tons of enhancements. He&#8217;s also stayed fairly current on releasing updates to the theme. Now both the lite and pro versions are at version 2.0.2 and come with some bells & whistles that just weren&#8217;t available when I started using Autofocus.

Even with all of those updates, enhancements, etc&#8230; I just didn&#8217;t like the direction AutoFocus was going. I was stuck in its 1.x days and loving the way it worked. I love the simplicity, lack of widgets, and overall minimalistic view of the theme. Needless to say, I never upgraded. I&#8217;ve made my own modifications to the theme throughout the time I&#8217;ve had it, and I like it just the way it is.  
<!--more-->

### The New Issues

So as the title (and the previous post I wrote about it) would suggest, I thought that the single post pages needed the thumbnails of the previous and next posts. I just thought it looked funny without them. With this idea, I set off to make that happen.  
[<img src="http://i2.wp.com/www.tquizzle.com/uploads/2009/11/Picture-2-198x300.png?fit=198%2C300" alt="" title="Zoomed Way Out to see the whole page" class="aligncenter size-medium wp-image-415" data-recalc-dims="1" />][2]  
Now while that was successful, many people in the comments of that post pointed out enhancements and fixes to my code. I welcomed that and modified it accordingly.

A couple of weeks ago while I was upgrading some other themes I was updating the very popular <a rel="nofollow" target="_blank" href="http://www.binarymoon.co.uk/projects/timthumb/">TimThumb</a> script. It is used for dynamic re-sizing of images and has been very successful in doing so in many WordPress themes. I thought to myself, why not utilize this script in AutoFocus? Why didn&#8217;t I think of that before?

Now what I have is a post image thumbnail where I supply what I want TimThumb to resize the height to, and it adjusts the width proportionality. TimThumb also has a whole host of other settings it can do. I suggest you <a rel="nofollow" target="_blank" href="http://www.binarymoon.co.uk/2010/08/timthumb/" title="Using TimThumb part 1: Getting Started">check it out</a> and see for yourself.

### The New Solution

So what I&#8217;ve done now is revamped the way the previous/next post thumbnail gets displayed as well as turning the code into a function so I can just plop it into my single.php file.

1.  First things first, go grab TimThumb and copy it into your theme directory. Rename this file thumb.php (if you&#8217;re following my example exactly) or edit the call to it on line 18 and 36.
2.  Paste the following function into your theme&#8217;s *functions.php* file. <pre class="brush: php; collapse: false; highlight: [16,17,18,19,20,21,22,34,35,36,37,38,39,40]; title: ; toolbar: false; wrap-lines: true; notranslate" title="">/*
  Previous / Next Post Image Thumbnails
*/

function tq_prev_next_post() {

		echo '&lt;div id="nav-below" class="navigation"&gt;';

		$previouspost = get_previous_post($in_same_cat, $excluded_categories);
 
		if ($previouspost != null) {
			echo '&lt;div class="nav-previous"&gt;';
			previous_post_link('%link &laquo; Previous');
			echo '&lt;div class="nav-excerpt"&gt;&lt;p&gt;';
 
			/* Show previous Post's Thumbnail */
			$tq_previouspost_img = get_post_meta($previouspost-&gt;ID, "image_url", $single = true);
			$tq_previouspost_img = get_bloginfo('template_url') . "/thumb.php?src=" . $tq_previouspost_img . "&h=150&q=70&s=1";
			$tq_previouspost_title = get_post($previouspost-&gt;ID);
			$tq_previouspost_title = $tq_previouspost_title-&gt;post_title;
			echo '&lt;img class="post-thumb alignleft size-thumbnail" src="' . $tq_previouspost_img . '" alt="' . $tq_previouspost_title . '" /&gt;';
			/* End previous thumbnail */			
 
			previous_post_excerpt();
			echo '&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;';
		} 
		$nextpost = get_next_post($in_same_cat, $excluded_categories);
 
		if ($nextpost != null) {
			echo '&lt;div class="nav-next"&gt;';
			next_post_link('&lt;span style="text-align:right;"&gt;Next &raquo; %link &lt;/span&gt;');
			echo '&lt;div class="nav-excerpt"&gt;&lt;p&gt;';
 
			/* Show Next Post's Thumbnail */
			$tq_nextpost_img = get_post_meta($nextpost-&gt;ID, "image_url", $single = true);
			$tq_nextpost_img = get_bloginfo('template_url') . "/thumb.php?src=" . $tq_nextpost_img . "&h=150&q=70&s=1";
			$tq_nextpost_title = get_post($nextpost-&gt;ID);
			$tq_nextpost_title = $tq_nextpost_title-&gt;post_title;
			echo '&lt;img class="post-thumb alignright size-thumbnail" src="' . $tq_nextpost_img . '" alt="' . $tq_nextpost_title . '" /&gt;';
			/* End Next thumbnail */			
 
			next_post_excerpt();
			echo '&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;';
		}
		echo '&lt;/div&gt;&lt;!-- #nav-below --&gt;';
}</pre>

3.  Edit your *single.php* file. You&#8217;re going to replace the <pre class="brush: xml; light: true; title: ; notranslate" title="">&lt;div id="nav-below"&gt; ... &lt;/div&gt;</pre>
    
    section with the function we just created. Replace it with <pre class="brush: php; light: true; title: ; notranslate" title="">&lt;?php tq_prev_next_post(); ?&gt;</pre></li> </ol> 
    
    That&#8217;s it. Again it would be best if you have any questions to first look at my [original post][1] as to where these chunks of code go and how the overall code block should look.
    
    Here&#8217;s what it looks like now.  
    [<img src="http://i0.wp.com/www.tquizzle.com/uploads/2012/06/autofocus_preview_2-300x86.jpg?fit=300%2C86" alt="" title="AutoFocus Preview 2" class="aligncenter size-medium wp-image-11492" data-recalc-dims="1" />][3]
    
    You can also see it in action by visiting my <a rel="nofollow" target="_blank" href="http://photos.tquizzle.com">Photoblog</a>.
    
    <div class="sharedaddy sd-sharing-enabled">
      <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
        <h3 class="sd-title">
          Share this:
        </h3>
        
        <div class="sd-content">
          <ul>
            <li class="share-twitter">
              <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-11477"><span>Twitter</span></a>
            </li>
            <li class="share-google-plus-1">
              <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-11477"><span>Google</span></a>
            </li>
            <li class="share-facebook">
              <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/?share=facebook" title="Share on Facebook" id="sharing-facebook-11477"><span>Facebook</span></a>
            </li>
            <li class="share-custom">
              <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
                  <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-11477"><span>LinkedIn</span></a>
                </li>
                <li class="share-reddit">
                  <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
                </li>
                <li class="share-end">
                </li>
                <li class="share-digg">
                  <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
                </li>
                <li class="share-stumbleupon">
                  <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
                </li>
                <li class="share-end">
                </li>
                <li class="share-email">
                  <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/?share=email" title="Click to email this to a friend"><span>Email</span></a>
                </li>
                <li class="share-print">
                  <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/autofocus-previous-post-next-post-image-thumbnails/" title="Click to print"><span>Print</span></a>
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

 [1]: http://www.tquizzle.com/archive/previous-post-next-post-image-thumbnails/ "Previous Post / Next Post Image Thumbnails using Autofocus"
 [2]: http://i1.wp.com/www.tquizzle.com/uploads/2009/11/Picture-2.png
 [3]: http://i0.wp.com/www.tquizzle.com/uploads/2012/06/autofocus_preview_2.jpg