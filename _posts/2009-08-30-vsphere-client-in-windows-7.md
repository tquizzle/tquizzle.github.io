---
title: vSphere Client in Windows 7
author: TQuizzle
layout: post
permalink: /archive/vsphere-client-in-windows-7/
image:
  - 
bitly_url:
  - http://bit.ly/12KaZCw
bitly_hash:
  - 12KaZCw
bitly_long_url:
  - http://www.tquizzle.com/archive/vsphere-client-in-windows-7/
categories:
  - Normal
tags:
  - ESX
  - ESXi
  - vSphere
  - Windows 7
  - workaround
---
While I mostly use a PC at work and a Mac at home, occasionally I use my &#8220;other&#8221; laptop. That special one who only gets powered on a couple of times a month to do random and various tasks and as the title would suggest, it&#8217;s running Windows 7.

So, I have an ESXi 4.0 server here at home that runs a Linux server, a windows 2003 server and other various guest OS flavors. As of ESX 4.0, the client was renamed and updated to vSphere Client instead of vMWare Infrastructure Client. That client piece is the piece that lets you modify your ESX host and all of its virtual machines, datastores, network, etc&#8230;

As luck would have it&#8230;the client doesn&#8217;t work under Windows 7. Blast! You get this error:   
**Error parsing the server &#8220;SERVER IP&#8221; &#8220;clients.xml&#8221; file.**

With Google and a little patience, I got it working again &#8211; for the first time.<a rel="shadowbox" href="http://i2.wp.com/www.tquizzle.com/uploads/2009/08/ESX.jpg"><img src="http://i0.wp.com/www.tquizzle.com/uploads/2009/08/ESX-300x212.jpg?fit=300%2C212" alt="ESX" title="ESX" class="alignright size-medium wp-image-339" data-recalc-dims="1" /></a>

Here&#8217;s a little rundown of how to get VMWare&#8217;s latest client product to work under Windows 7:  

  
For starters, your system needs a file from Microsoft&#8217;s .NET Framework on an earlier system of Windows. *I got mine from an XP machine.*

1.  Obtain a copy of *`%SystemRoot%\\Microsoft.NET\\Framework\\v2.0.50727\\System.dll`* from a Windows Vista or below that has .NET 3.5 SP1 installed.
2.  Create a folder on your Windows 7 machine where the vSphere client is installed and copy the file from step 1 into this folder. For example, create the folder under the vSphere client launcher installation directory *`(%ProgramFiles%\\VMware\\Infrastructure\\Virtual Infrastructure Client\\Launcher\\Lib+)`*. 
3.  Now we need to tell the vSphere client that we&#8217;re going to run the product in Development mode. So, in the vSphere client launcher directory, open the VpxClient.exe.config file in a text editor and add a <runtime> element and a <developmentMode> element as shown below. Save the file.  
    `<br />
<configuration><br />
...<br />
<runtime><br />
<developmentMode developerInstallation="true"/><br />
</runtime><br />
</configuration><br />
` 
4.  Create a batch/cmd file (e.g. \*VpxClient.cmd\*) in the same location. In this file add a command to set the DEVPATH environment variable to the folder where you copied the System.dll assembly in step 2 and a second command to launch the vSphere client.  
    `<br />
SET DEVPATH=%ProgramFiles%\\VMware\\Infrastructure\\Virtual Infrastructure Client\\Launcher\\Lib<br />
"%ProgramFiles%\\VMware\\Infrastructure\\Virtual Infrastructure Client\\Launcher\\VpxClient.exe"` 
5.  Replace the shortcuts in the start menu to point to the batch file created in the previous step. Change the shortcut properties to run minimized so that the command window is not shown.  
    You can now use the VpxClient.cmd (or the shortcut) to launch the vSphere client in Windows 7. 

*Note that this workaround bypasses the normal .NET Framework loading mechanism so that assembly versions in the DEVPATH folder are no longer checked.* </blockquote> 

<small>Big up to <a rel="nofollow" target="_blank" href="http://communities.vmware.com/people/ftubio;jsessionid=D2A4A2E6D4324376F529A4CDE864FFC7">Fernando</a> from the VMWare Communities forum for writing this up. I changed a few things form his original post but follow these steps and you&#8217;ll vSphering in Windows 7.</small>

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow" class="share-twitter sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/?share=twitter" title="Click to share on Twitter" id="sharing-twitter-327"><span>Twitter</span></a>
        </li>
        <li class="share-google-plus-1">
          <a rel="nofollow" class="share-google-plus-1 sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/?share=google-plus-1" title="Click to share on Google+" id="sharing-google-327"><span>Google</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow" class="share-facebook sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/?share=facebook" title="Share on Facebook" id="sharing-facebook-327"><span>Facebook</span></a>
        </li>
        <li class="share-custom">
          <a rel="nofollow" class="share-custom sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/?share=custom-1371173110" title="Click to share"><span style="background-image:url(&quot;http://www.repost.us/wp-content/themes/repost-beta/repost-site/favicon.ico&quot;);">repost</span></a>
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
              <a rel="nofollow" class="share-linkedin sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/?share=linkedin" title="Click to share on LinkedIn" id="sharing-linkedin-327"><span>LinkedIn</span></a>
            </li>
            <li class="share-reddit">
              <a rel="nofollow" class="share-reddit sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/?share=reddit" title="Click to share on Reddit"><span>Reddit</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-digg">
              <a rel="nofollow" class="share-digg sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/?share=digg" title="Click to Digg this post"><span>Digg</span></a>
            </li>
            <li class="share-stumbleupon">
              <a rel="nofollow" class="share-stumbleupon sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/?share=stumbleupon" title="Click to share on StumbleUpon"><span>StumbleUpon</span></a>
            </li>
            <li class="share-end">
            </li>
            <li class="share-email">
              <a rel="nofollow" class="share-email sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/?share=email" title="Click to email this to a friend"><span>Email</span></a>
            </li>
            <li class="share-print">
              <a rel="nofollow" class="share-print sd-button share-icon" href="http://www.tquizzle.com/archive/vsphere-client-in-windows-7/" title="Click to print"><span>Print</span></a>
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