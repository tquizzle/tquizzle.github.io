---
title: How To Move Critical Windows Folders to Other Local Disks
author: TQuizzle
layout: post
permalink: /archive/how-to-move-critical-windows-folders-to-other-local-disks/
pdrp_attributionLocation:
  - caption
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
  - http://bit.ly/12KaZCs
bitly_hash:
  - 12KaZCs
bitly_long_url:
  - http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/
categories:
  - Normal
tags:
  - folders
  - geeky
  - hard links
  - symlinks
  - system
  - Windows 7
  - windows administration
---
[<img src="http://i1.wp.com/www.tquizzle.com/uploads/2012/12/Moving-Users-and-Prog-Files-300x192.png?fit=300%2C192" alt="Moving Users and Prog Files" class="alignleft size-medium wp-image-11576" data-recalc-dims="1" />][1]If you&#8217;ve ever needed or tried to move the C:&#92;Users directory or other default Windows® directories to another place other than the default one, you know it can be quite difficult.

I&#8217;ve tried to Google this, and talk to others about doing it. What seemed to be such a simple request also seemed to be difficult to pull off. That&#8217;s when a brilliant (nearly the smartest man I know) told me about<a rel="nofollow" target="_blank" title="Hard Links and Junctions" href="http://msdn.microsoft.com/en-us/library/windows/desktop/aa365006(v=vs.85).aspx"> hard links & junction links</a> in windows. Think of them like symbolic links in Mac or *nix systems.

*   C:&#92;dira linked to C:&#92;dirb
*   D:&#92;dir1&#92; to C:&#92;dir2&#92;dir3

The great thing about using hard links in Windows is that it acts as if the data is still there. In the example above, when you&#8217;re browsing C:&#92;dira the system will act as if you&#8217;re really in that directory when in all reality you&#8217;re browsing C:&#92;dirb. Even the address bar will show that.

Thanks to an almost 3-year-old post on&nbsp;<a rel="nofollow" target="_blank" title="Move the Users Directory in Windows 7" href="http://lifehacker.com/5467758/move-the-users-directory-in-windows-7">Lifehacker</a>, I accomplished what I thought was only possible with tons of registry tweaking and tons of time spent in Safe Mode with a potentially unstable system afterward.  
<!--more-->

### Real Reason Why

So the real reason I needed to so this is that I wanted to totally rebuild my system. New parts, new paint. Start from scratch and make this new Windows 7 installation as fast as it could be. Thanks to a good friend, I was given a small 30GB SSD. Now I could have run Windows on this just fine and had some programs installed there and others installed on another disk. Maybe even copied my music, downloaded programs, etc&#8230; to this other disk. But that requires that every time an installer runs I have to pay close attention to where it&#8217;s going. Every time a program wants to move data into the &#8220;My Documents&#8221; folder, I have to be mindful that I&#8217;m only dealing with about 18GB free after a clean install. That&#8217;s simply not enough. I&#8217;d run out in less than a few weeks and many times probably forget that these installers are putting all their files into the C:&#92;Program Files directory.

### Step-By-Step

So here&#8217;s the step-by-step instructions to moving just about any folder to another disk, especially those special Windows ones.

#### Install & Create Restore Point

1.  Install a fresh copy of Windows 7 (or XP or 8, whatever you want)
2.  Dont do anything else. Just leave it fresh and clean.
3.  Create a Restore Point (just to play it safe) 
    1.  Right Click &#8220;My Computer&#8221; and choose Properties
    2.  Choose &#8220;System Protection&#8221;
    3.  Select the &#8220;System Protection&#8221; Tab
    4.  Click Create
    5.  Type a description for this Restore
    6.  Click Create

#### System Recovery

1.  Boot back up with the install DVD
2.  Choose the appropriate language, currency & keyboard and click Next
3.  At the screen where there is a large &#8220;Install Now&#8221; button, look just below it and click &#8220;Repair your computer&#8221;
4.  You might be asked if you want to &#8220;Repair and Restart&#8221;, choose No.
5.  Make sure that the OS that system recovery found is the one you just installed and that it&#8217;s selected. Click Next.
6.  You&#8217;ll be presented with a few options&#8230;choose &#8220;Command Prompt&#8221;

Now here&#8217;s where we really get our hands dirty. Well, not really, but just a bit.

Find out which drives are what.

Install Drive: DVD  
OS Drive: Source  
Secondary Drive: Destination

On my computer, it was:

X: DVD Install Drive  
E: Actual OS SSD Drive  
D: Secondary Hard Drive

#### Copy Data & Create Hard Links

So at this point, you need to copy all the source data to the destination drive and create the hard links.

Using my drive letters above, here is how its done.

1.  robocopy /copyall /mir /xj E:&#92;Users D:&#92;Users
2.  robocopy /copyall /mir /xj &#8220;E:&#92;Program Files&#8221; &#8220;D:&#92;Program Files&#8221;
3.  robocopy /copyall /mir /xj &#8220;E:&#92;Program Files (x86)&#8221; &#8220;D:&#92;Program Files (x86)&#8221;

<span class="shortcode-highlight">/mir tells Robocopy to mirror the directories. This will copy all files and their permissions<br /> /xj is very important as well as it tells Robocopy to now follow any junctions points it might meet when browsing these locations.<strong> Don&#8217;t Forget This</strong></span><!--/.shortcode-highlight-->

Now as long as no files failed to copy, we can proceed.

In order to create junctions or hard links, the source folder must not exist. This means that we now have to delete those directories we just copied.

1.  <span style="line-height: 13px;">rmdir /S /Q E:&#92;Users</span>
2.  rmdir /S /Q &#8220;E:&#92;Program Files&#8221;
3.  rmdir /S /Q &#8220;E:&#92;Program Files (x86)&#8221;

Now we create the NTFS Junction/symlinks

1.  mklink /J E:&#92;Users D:&#92;Users
2.  mklink /J&nbsp;&#8220;E:&#92;Program Files&#8221; &#8220;D:&#92;Program Files&#8221;
3.  mklink /J&nbsp;&#8220;E:&#92;Program Files (x86)&#8221; &#8220;D:&#92;Program Files (x86)&#8221;

Now you&#8217;ve just moved all three of these folders from the Windows system disk to another disk.

### Prove it to yourself

Now comes the proof. Change directories to E:&#92;. Type dir and see what you see. You should see &#8221; Users [D:&#92;Users]&#8221;

Now restart your computer and you&#8217;re done.

Congratulations!

### Update

A while after doing this Windows Update started failing on a few updates. I kept receiving the following error: Windows update error 80070011

I found that Microsoft® isn&#8217;t following those symlinks properly when it comes to certain security updates. I think had I only moved the &#8220;Users&#8221; directory all would be fine.

Google is my friend and I found out what needed to change in order for security updates to continue.  
Basically, there are a few registry keys you&#8217;ll need to point to the &#8220;real&#8221; location of the Program Files directory because it wont follow the junction link.

Make these changes:  
HKEY\_LOCAL\_MACHINE&#92;SOFTWARE&#92;Microsoft&#92;Windows&#92;CurrentVersion&#92;

<div class="threecol-one">
  <strong>Key Name</strong>
</div>

<div class="threecol-one">
  <strong>Old Data Value</strong>
</div>

<div class="threecol-one last">
  <strong>New Data Value</strong>
</div>

* * *

<div class="threecol-one bold">
  CommonFilesDir
</div>

<div class="threecol-one bold">
  C:&#92;Program Files&#92;Common Files
</div>

<div class="threecol-one last bold">
  D:&#92;Program Files&#92;Common Files
</div>

<div class="threecol-one bold">
  CommonFilesDir (x86)
</div>

<div class="threecol-one bold">
  C:&#92;Program Files (x86)&#92;Common Files
</div>

<div class="threecol-one last bold">
  D:&#92;Program Files (x86)&#92;Common Files
</div>

<div class="threecol-one bold">
  CommonW6432Dir
</div>

<div class="threecol-one bold">
  C:&#92;Program Files&#92;Common Files
</div>

<div class="threecol-one last bold">
  D:&#92;Program Files&#92;Common Files
</div>

<div class="threecol-one bold">
  ProgramFilesDir
</div>

<div class="threecol-one bold">
  C:&#92;Program Files
</div>

<div class="threecol-one last bold">
  D:&#92;Program Files
</div>

<div class="threecol-one bold">
  ProgramFilesDir (x86)
</div>

<div class="threecol-one bold">
  C:&#92;Program Files (x86)
</div>

<div class="threecol-one last bold">
  D:&#92;Program Files (x86)
</div>

<div class="threecol-one bold">
  ProgramW6432Dir
</div>

<div class="threecol-one bold">
  C:&#92;Program Files
</div>

<div class="threecol-one last bold">
  D:&#92;Program Files
</div>

After these changes are made, Windows should be able to update successfully.

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-11569"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-11569"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/?share=facebook" title="Share on Facebook" id="sharing-facebook-11569"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-11569"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/how-to-move-critical-windows-folders-to-other-local-disks/" title="Click to print"><span>Print</span></a>
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

 [1]: http://i1.wp.com/www.tquizzle.com/uploads/2012/12/Moving-Users-and-Prog-Files.png