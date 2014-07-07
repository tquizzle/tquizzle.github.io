---
title: Google Document Viewer for WordPress
author: TQuizzle
layout: post
permalink: http://bit.ly/10hfRgI
image:
  - http://www.tquizzle.com/uploads/2010/08/goo_doc_viewer.jpg
pdrp_attributionLocation:
  - end
pdrp_attributionExtended:
  - 1
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
  - http://bit.ly/10hfRgI
bitly_hash:
  - 10hfRgI
bitly_long_url:
  - http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/
categories:
  - Normal
tags:
  - code
  - display
  - document
  - Google
  - iframe
  - pdf
  - ppt
  - tiff
  - viewer
  - WordPress
---
I actually read about this little feature a while back&#8230;like almost a year or so ago. I thought it was a neat feature, I just really had no use for it.

Recently though, I wanted to embed a PDF into a webpage and remembered seeing <a rel="nofollow" target="_blank" href="http://googlesystem.blogspot.com/2009/09/embeddable-google-document-viewer.html">this article</a> from last year. I immediately went out to create a simple, useful function to be able to use this in WordPress.

<!--more-->

After jacking with the code for a bit, I ran it by <a rel="nofollow" target="_blank" href="http://justinshattuck.com">Shat</a> who always helps fix up my code. He tweaked it, and stripped out extraneous code that I had to make it easier to use. Thus, Shat and I present the Google Document Viewer functions hack.

Add this to your functions.php file and you&#8217;re in business to use the Google Document Viewer shortcode to display a PDF, PPT, or a TIFF file inline.

### Functions Code

<pre class="brush: php; collapse: false; title: ; toolbar: false; wrap-lines: true; notranslate" title="">/*
Title: Google Document Viewer in WordPress
Author: Travis Quinnelly &amp; Justin Shattuck
AuthorURI: http://www.tquizzle.com

Usage: You can use this by adding this to your functions.php file in your WordPress theme directory and passing it variables.
	1. path to document (.ppt, .pdf, .tiff) * Mandatory
	2. iframe width in pixels
	3. iframe height in pixels
	4. any inline CSS styling elements you wish
*/
function google_doc_viewer($atts, $content = null) {
   extract(shortcode_atts(array(
      "width" =&gt; '600',
      "height" =&gt; '800',
      "path" =&gt; '',
      "style" =&gt; ''
   ), $atts));
   return '
&lt;iframe style="'.$style.'" src="http://docs.google.com/viewer?url='.$path.'&embedded=true" frameborder="0" width="'.$width.'" height="'.$height.'"&gt;&lt;/iframe&gt;';
}
add_shortcode("docview", "google_doc_viewer");</pre>

### Usage

We&#8217;ve made it simple to use, just like all other shortcodes. And by simple, I mean simple! As you see above, the width, height, path, and style are all things to pass to the shortcode. The only one that&#8217;s obviously mandatory is the path. The function already sets some height/width settings and those are easily changed in your function. I like 600X800 so that&#8217;s what the default here is.

Simply type: **&#91;docview width=&#8221;*yourvalue*&#8221; height=&#8221;*yourvalue*&#8221; path=&#8221;*pathtofile*&#8221; style=&#8221;*extrainlinestyle*&#8220;]**

#### Usage variables

*   width = enter specific width you&#8217;d like if it differs from the default values
*   height = enter specific height you&#8217;d like if it differs from the default values
*   path = enter full url path to document to render ***mandatory**
*   style = enter any extra inline styling you&#8217;d like added to the iframe html element

### Example

Here&#8217;s an example of my code in use with &#8220;The Anatomy of a Large-Scale Hypertextual Web Search Engine&#8221; by the now infamous Sergey Brin and Lawrence Page.  


<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-2688"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-2688"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/?share=facebook" title="Share on Facebook" id="sharing-facebook-2688"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-2688"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/google-document-viewer-for-wordpress/" title="Click to print"><span>Print</span></a>
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