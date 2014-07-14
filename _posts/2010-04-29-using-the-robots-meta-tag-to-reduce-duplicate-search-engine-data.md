---
title: Using the Robots Meta Tag to Reduce Duplicate Search Engine Data
author: TQuizzle
layout: post
permalink: /archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/
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
  - http://bit.ly/10hfR0m
bitly_hash:
  - 10hfR0m
bitly_long_url:
  - http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/
categories:
  - Normal
tags:
  - functions
  - meta
  - php
  - robots
  - search engine
  - theme
  - Thesis
  - WordPress
---
<img src="/uploads/2010/04/search_engines-300x293.jpg?fit=300%2C293" alt="" title="Search Engines" class="alignright size-medium wp-image-602" data-recalc-dims="1" /><a rel="nofollow" target="_blank" href="http://www.pearsonified.com/">Chris Pearson</a> is a stud when it comes to all things web, not to mention the guy&#8217;s relentless pursuit of wordpress goodness keeps me coming back to his blog again and again.  
Yesterday morning, <a rel="nofollow" target="_blank" href="http://diythemes.com/thesis/robots-meta-tags/">a post from him via DIYThemes.com</a> grabbed my attention. It was all about how to use the Robots Meta Tags option in the very popular theme <a rel="nofollow" target="_blank" href="http://diythemes.com/plans/">Thesis</a>. While I dont use Thesis, I still found it extremely interesting and started to investigate its declaration:

> One of the biggest problems with WordPress is that it automatically generates different kinds of archive pages that can be indexed by search engines. From date-based archives (daily, monthly, yearly) to tags to categories, these auto-generated pages all contain duplicate content that doesn't belong in search engines.

Like many times before, he&#8217;s exactly right.  
  
Maybe you don&#8217;t think its a big deal. Okay, I get that&#8230;but think of this:

> The job of search engines is to index your site's pages and determine what your site is about. If you have 100 unique article pages, then ideally, search engines should only have to crawl 100 pages to index your site fully.
> 
> However, if you're using categories, tags, and date-based archives (and depending on how overboard you tend to go with categorization and tagging), then you're going to have at least one additional page per category, per tag, per month, etc.
> 
> Now, instead of having 100 pages to index, you may have 600 pages. Considering you only have 100 pages of unique content, forcing a search engine to index 600 pages to determine what your site is about just doesnâ€™t make any sense.
> 
> Think of it this way: Would you rather read a 100-page book or a 600-page book that tells the same story? Further, which one do you think you'll understand better? Which will hold your focus better?

Wow, now that&#8217;s heavy.

### Functions Hack

So since its implemented with Thesis so beautifully, and since I love to hack my functions.php file&#8230;I figured, I&#8217;d do just that. I&#8217;d put together a super-tiny function that fixes this, albeit small, issue for my specific customization.

<pre class="brush: php; title: ; toolbar: false; notranslate" title="">// META ROBOTS functions.php hack for proper indexing by Search Engines

function tq_meta_robots() {
// If you would like to disable the ODP or Yahoo! Directory
// keep the next two lines.
if( is_home() )
echo '&lt;meta name="robots" content="index,follow,archive,noodp,noydir" /&gt;';
if( is_archive() || is_tax() ) 
echo '&lt;meta name="robots" content="index,nofollow,noarchive" /&gt;';
}
add_action('wp_head','tq_meta_robots');
</pre>

There&#8230;that&#8217;ll do it.

The first part checks to see if its the home page (since &#8220;*noodp*&#8221; and &#8220;*noydir*&#8221; are domain specific settings), then sets the proper search engine robot setting to allow indexing, link following, archiving and prevents search engines from pulling extra information regarding your site from the <a rel="nofollow" target="_blank" href="http://www.dmoz.org/">ODP or DMOZ</a> and the <a rel="nofollow" target="_blank" href="http://dir.yahoo.com">Yahoo! Directory</a>.  
The second part checks to see if the page is any archive type page (Category, Tag, Author and Date based pages are all types of Archives), or any taxonomy related pages; and sets the information for those types of pages. This sets the search engine robot setting to allow indexing, tells it that links are to NOT be followed, and to not archive the page.

Done and Done.

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-594"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-594"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/?share=facebook" title="Share on Facebook" id="sharing-facebook-594"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-594"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/using-the-robots-meta-tag-to-reduce-duplicate-search-engine-data/" title="Click to print"><span>Print</span></a>
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