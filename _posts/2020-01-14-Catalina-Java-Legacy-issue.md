---
title: "Solve the Annoying Java Legacy Issue on Catalina"
layout: post
date: 2020-01-14
tag:
- dev
blog: true
star: false
---

<span class='fl'>M</span>an, I thought it was quite smooth, almost couldn't believe it, that I didn't run into any issues while upgrading macOS from Mojave to Catalina on my machine. although it did created some annoying files during the installation, I sure can deal with it especially when I knew I could throw them to trash at almost no cost after a litte research.

The inner peace of software doesn’t settle long, the problem arises, the notorious Java Command-line Popup comes back again.

<div class="sec-img">
  <img class="post-img" src="../assets/images/to-use-java-command-line.png">
  <p class="caption">Here you go, one of the most notorious things knows on macOS</p>
</div>

It is because some of the applications you are running depend on some denpendencies form a older version of Java. So, Apple has an offical fix for it at [ here ](https://support.apple.com/kb/dl1572?locale=en_US), it will install those certain dependencies for you to solve the problem. However, that only works if you aren't on Catalina. Catalina has an issue addresses is in regard to ENVI/IDL's current dependency on legacy Java 6 libraries, see [details](https://www.harrisgeospatial.com/Support/Self-Help-Tools/Help-Articles/Help-Articles-Detail/ArtMID/10220/ArticleID/23780/Mac-OS-Catalina-1015-ENVIIDL-and-Legacy-Java-6-Dependencies).

<div class="sec-img">
  <img class="post-img" src="../assets/images/cannot-install-java2017.png">
  <p class="caption">On Catalina, you can't simple install the older version of Java</p>
</div>

I tried to follow [this link](https://www.harrisgeospatial.com/Support/Self-Help-Tools/Help-Articles/Help-Articles-Detail/ArtMID/10220/ArticleID/23780/Mac-OS-Catalina-1015-ENVIIDL-and-Legacy-Java-6-Dependencies) remove all the newer Java on my machine, so I could install the compatible one first, then come back to install the newer one, well it didn't work as expected, it still said the same thing.

Then I saw [ this ](https://www.harrisgeospatial.com/Support/Self-Help-Tools/Help-Articles/Help-Articles-Detail/ArtMID/10220/ArticleID/23780/Mac-OS-Catalina-1015-ENVIIDL-and-Legacy-Java-6-Dependencies), followed the guide to add scripts into the script editor, after compiled it, then executed it. But for some reason, it didn't work either, the script didn't work.

I finally found a working solution [here](https://discussions.apple.com/thread/250853223), follow the guide, you should be able to go.


### References

* https://discussions.apple.com/thread/250853223
* https://www.harrisgeospatial.com/Support/Self-Help-Tools/Help-Articles/Help-Articles-Detail/ArtMID/10220/ArticleID/23780/Mac-OS-Catalina-1015-ENVIIDL-and-Legacy-Java-6-Dependencies
* https://discussions.apple.com/thread/250735756
* https://www.oracle.com/technetwork/java/javase/downloads/jdk13-downloads-5672538.html