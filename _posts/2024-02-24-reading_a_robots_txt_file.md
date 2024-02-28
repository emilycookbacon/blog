---
layout: post
title:  "Reading a robots.txt file"
date:   2024-02-24
description: "A quick introduction on how to read a robots.txt file"
# image: "/assets/img/image5.jpg"
display_image: false  # change this to true to display the image below the banner 
---


<p class="intro"><span class="dropcap">T</span>his post will describe the importance of using a `robots.txt` file, where to find it, how to read a it, examples, and show a few hidden gems on the internet. This is particularly important for anyone wanting to learn how to ethically web scrape.</p>

### Why does a robots.txt file matter?

The purpose of `robots.txt` file is to communicate what rules the website creator would like you to follow when scraping their website. You might be thinking, "I'm not a robot, so why should I care about this at all?" While you might not be a robot yourself, if you are writing code to gather online information then these guidelines would apply. It is, afterall, your program that is pulling the information for you. While there is no legal obligation to follow the guidelines set in the `robots.txt` file, it is important for ethical web scraping to respect the bounds the host has said. They might want to block certain users or files for privacy and security. They might want to delay access so it doesn't impact other site users. It is within the host's discretion to block certain users from accessing their site. Let me first explain where you might access one to look at. 

### Where robots.txt is located
On any given website when you are on the home page, typically the website url starts with `http://`, has the name of the website and the ends in a  `.com`, `.edu`, `.gov` or something of the like. The After said url, tack on `/robots.txt` and the information for the web scraping guidelines should come right up. This post will go through some examples, but first let me explain some things you might see.

### Robots.txt content

1. The `User-Agent: ` specifies users or bots and the following lines would typically describe what that specific user can or cannot do. The typed words would specifically say `user-agent` followed by a colon, space, and then the specific user. Unless otherwise specified, if you see `User-Agent: *` that would mean everyone is included.


2. `Disallow: ` indicates file paths not allowed. These begin with a `/` and have following information. Any time `*` is used, it indicates it can be anything up until this point. A path you might see is `/*images/*` indicating that no images should be accessed. If the only content after disallow is `/`, then a web scraper should not be used.

3. `Allow: ` indicates file paths that are allowed. This is not as common as disallow lines and does have the same format. 

4. `Crawl-delay: ` indicates the amount of time (in seconds) the crawler should wait between requests. 

5. `Sitemap: ` is a link to the XML file that holds the blueprint to the website. This helps seach engines find, crawl, and index all of the website's content and indicates where important areas to scape might be. 

### Examples
Any of the following examples are based on when this post was published and may have been altered since then. Always check what the current robots.txt file says. 

1. Expo Markers Example
For example if we look at the website for [Expo Markers](https://www.expomarkers.com/robots.txt), at we would get the following text:

{% raw %} User-Agent: *
Allow: /
 
Disallow: /*cart
Disallow: /account/
Disallow: /setpassword/
Disallow: /search*
Disallow: /confirmednewpassword/
Disallow: /profile/
Disallow: /orders/

sitemap: https://www.expomarkers.com/sitemap_index.xml{% endraw %}

We can see here that for most people, everything is allowed except for a some things mostly pertaining to the account, cart, or orders and they do have a sitemap. 

### Hidden Gems

While the `robots.txt` file is typically a simple text document with no formatting, by adding a comment line (starting a line with #), it can be more personalized. Let me show two `robots.txt` with interesting comments that I have found. 

1. [Nike](https://www.nike.com/robots.txt) found a way to brand their own text document. 
![Figure]({{site.url}}/{{site.baseurl}}/assets/img/nike.png)

2. [Wikipedia](https://en.wikipedia.org/robots.txt) has included comments that sound like a scolding mother. 


### Conclusion

While the purpose of this post is to teach you how to locate and read a robots.txt file and show a few examples, it doesn't mean much unless you explore and find one you would want to use yourself. So after all this, I ask you reader, what `robots.txt` files do you want to find? Now spend a bit of time looking at it. 


