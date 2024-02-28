---
layout: post
title:  "Reading a robots.txt file"
date:   2024-02-24
description: "How to read a robots.txt file and finding some internet gems"
# image: "/assets/img/image5.jpg"
display_image: false  # change this to true to display the image below the banner 
---


<p class="intro"><span class="dropcap">T</span>his post will describe the importance of using a `robots.txt` file, where to find it, how to read a it, examples, and show a few hidden gems on the internet. This is particularly important for anyone wanting to learn how to ethically web scrape.</p>

To ethically web scrape, you first need to be familiar with what a robots.txt is and what it contains. This blog post will explain why a `robots.txt` matters, where to find one, what is in its contents, and show some internet gems. 

### Why does a robots.txt file matter?

The purpose of `robots.txt` file is to communicate what rules the website creator would like you to follow when scraping their website. It is to help manage crawler traffic. You might be thinking, "I'm not a robot, so why should I care about this at all?" While you might not be a robot yourself, if you are writing code to gather online information then these guidelines would apply. It is, afterall, your program that is pulling the information for you. 

While there is no legal obligation to follow the guidelines set in the `robots.txt` file, it is important for ethical web scraping to respect the bounds the host has said. They might choose to block certain users or files for privacy and security or they might want to delay access so it doesn't impact other site users. It is within the host's discretion to block certain users from accessing their site. So let's get into it and locate on first.

### Where robots.txt is located
On any given website when you are on the home page, typically the website url starts with `http://`, has the name of the website and the ends in a  `.com`, `.edu`, `.gov` or something of the like. The url at this point is what we refer to as the baseurl. After said baseurl, tack on `/robots.txt` and the information for the web scraping guidelines should come right up. This post will go through some examples, but first let me explain some things you might see.

### Robots.txt content
The content of a `robots.txt` includes user-agent, disallow, allow, crawl-delay, and sitemap. Anything following this command would not be in quotations and would use regular expressions in their formatting.

1. The `User-Agent: ` specifies users or bots and the following lines would typically describe what that specific user can or cannot do. The typed words would specifically say `user-agent` followed by a colon, space, and then the specific user. Unless otherwise specified, if you see `User-Agent: *` that would mean everyone is included.


2. `Disallow: ` indicates file paths not allowed. These assume the baseurl and file paths written after the "Disallow: " will begin right after starting with a `/` and have following information. Any time `*` is used, it indicates it can be anything up until this point. A path you might see is `/*.pdf` indicating that no pdf documents should be accessed. If the only content after disallow is `/`, then a web scraper should not be used.

3. `Allow: ` indicates file paths that are allowed. This is not as common as disallow lines. This is similar to disallow where content following is tacked onto the baseurl, but is located after the "Allow: " does have the same format. 

4. `Crawl-delay: ` indicates the amount of time (in seconds) the crawler should wait between requests. Much like speed limit signs indicate the speed for traffic, this indicates the speed a web crawler should follow.

5. `Sitemap: ` is a link to the file that holds the blueprint to the website. It should include pages that are important for people to see and is often an XML file This helps seach engines find, crawl, and index all of the website's content and indicates where important areas to scape might be. What follows this line should be the whole url to where it is located. 

### Examples
Any of the following examples are based on when this post was published and may have been altered since then. Always check what the current robots.txt file says. 

1. Expo Markers 
For example if we look at the website for [Expo Markers](https://www.expomarkers.com/robots.txt), at we would get the following text:

{%- highlight txt -%} 
User-Agent: *
Allow: /
 
Disallow: /*cart
Disallow: /account/
Disallow: /setpassword/
Disallow: /search*
Disallow: /confirmednewpassword/
Disallow: /profile/
Disallow: /orders/

sitemap: https://www.expomarkers.com/sitemap_index.xml
{%- endhighlight -%}

We can see here that for most people, everything is allowed except for a some things mostly pertaining to the account, cart, or orders and they do have a sitemap. There is no crawl-delay so feel free to scrape as fast as you wish.

2. Nintendo 
For example if we look at the website for [Nintendo](https://www.nintendo.com/us/robots.txt), at we would get the text below by multiple sitemaps. For our purpose here, I have only included the top five sitemaps.

{%- highlight txt -%} 
User-agent: *
Disallow: /cart/
Disallow: /search/
Disallow: /orders/
Disallow: /*-*/orders/
Disallow: /wish-list/
Disallow: /*-*/wish-list/
Disallow: /address-book/
Disallow: /*-*/address-book/

Sitemap: https://noa-prod-graph-sitemaps.s3.amazonaws.com/nintendo.com/us/whatsnew/sitemap.xml
Sitemap: https://noa-prod-graph-sitemaps.s3.amazonaws.com/nintendo.com/us/nintendo-direct/sitemap.xml
Sitemap: https://noa-prod-graph-sitemaps.s3.amazonaws.com/nintendo.com/us/store/sitemap.xml
Sitemap: https://noa-prod-graph-sitemaps.s3.amazonaws.com/nintendo.com/us/news/sitemap.xml
Sitemap: https://noa-prod-graph-sitemaps.s3.amazonaws.com/nintendo.com/us/sitemap.xml
{%- endhighlight -%}

We can see here that for most people, everything is allowed except for anything relating to the orders, wish-list, address-book, cart, or search. Nintendo has many sitemaps listed for many country origins but I have listed just of the ones for the US here.

### Hidden Gems

While the `robots.txt` file is typically a simple text document with no formatting, by adding a comment line (starting a line with #), it can be more personalized. Let me show two `robots.txt` with interesting comments that I have found. 

1. [Nike](https://www.nike.com/robots.txt) found a way to brand their own text document. 
![Figure]({{site.url}}/{{site.baseurl}}/assets/img/nike.png)

2. [Wikipedia](https://en.wikipedia.org/robots.txt) has included comments that sound like a scolding mother that I found entertaining. Some of these comments I have put below, but by all means see if there are others yourself. Most of these comments are directed to specific user-agents. 

{%- highlight python -%} 
# Please note: There are a lot of pages on this site, and there are
# some misbehaved spiders out there that go _way_ too fast. If you're
# irresponsible, your access to the site may be blocked.
# Some bots are known to be trouble, particularly those designed to copy
# entire sites. Please obey robots.txt.
# Hits many times per second, not acceptable
# Friendly, low-speed bots are welcome viewing article pages, but not
# dynamically-generated pages please.
{%- endhighlight -%}

### Conclusion

While the purpose of this post is to teach you how to locate and read a robots.txt file and show a few examples, it doesn't mean much unless you explore and find one you would want to use yourself. So after all this, I ask you reader, what `robots.txt` files do you want to find? Now I invite you to go ahead and take a look for yourself.
