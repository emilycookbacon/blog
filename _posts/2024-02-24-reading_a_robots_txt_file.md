---
layout: post
title:  "Reading a robots.txt file"
date: 2024-02-24
description: 'A quick introduction on how to read a robots.txt file'
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

While the purpose of this post is to teach you how to locate and read a robots.txt file and show a few examples, it doesn't mean much unless you explore and find one you would want to use yourself. So after this, I ask you as the reader, what `robots.txt` files do you want to find?


### Steps for creating a new post.  

1. Create a new file in the `_posts` folder called `YYYY-MM-DD-post-name.md`, where YYYY is the year (2024), MM numeric month (01-12), and DD is the numeric day of the month (01-31).  The `post-name` is a short name for the new post with `-` between words.  **You must use this name convention for all new posts.**  

2. Make the YML heading.  All pages in the site need to start with a YML heading.  For posts you should use the following header:
```
---
layout: post
title:  "Post Name"
description: Short yet informative description
image: /assets/img/blog-image.jpg
---
```
*For this theme, the layout should stay as `post`.   All the other fields should be updated with the information for your particular blog post.*

3. If you add an image to the header information, the top banner picture will change for this post.  You can also add an optional field `display_image: true` if you want to display a larger image just below the header image.  If this happens, the banner image will return to the default.
  * The blog image should be a `.jpg` or `.png` file that can be found in `assets/img`.  Don't make it too large or the page will take longer to load (500-800 KB is a good size).  Leave the file path as `/assets/ing/` in the header area.* 
  * Adding a post image will also display the image in the "next" or "previous" post location.

4. Write the body of the blog using markdown.  There are a lot of references for markdown available.  I like the [Markdown Guide](https://www.markdownguide.org) because many of the examples show both the markdown and the html code.  There are separate pages for [basic syntax](https://www.markdownguide.org/basic-syntax/), [extended syntax](https://www.markdownguide.org/extended-syntax/), and a [cheatsheet](https://www.markdownguide.org/cheat-sheet/) for quick reference. 

---
---

### Links 

To create a link (internal or external), enclose the link text in brackets (e.g., [Statistics Department]) and then follow it immediately with the URL in parentheses (e.g., (https://statistics.byu.edu)).

For example:
```
{% raw %}My favorite department at BYU is the [Statistics Department](https://statistics.byu.edu).{% endraw %}
```
My favorite department at BYU is the [Statistics Department](https://statistics.byu.edu)


If you want external links to open in a separate window, you will need to use html code with `target="_blank"` inside the `a` tag. 

For example:
```
My favorite department at BYU is the <a href="https:statistics.byu.edu" target="_blank">Statistics Department</a>
```
My favorite department at BYU is the <a href="https:statistics.byu.edu" target="_blank">Statistics Department</a>


----
----

### Internal Links and Files

If you want to have a link that points to another location on your site or if you want to include a file (such as an image or video) you must use the `site.url` and `site.baseurl` variables when making the link reference.  For example, this link to pointing to the [About]({{site.url}}/{{site.baseurl}}/about) page is coded as:
```
[About]({% raw %}{{site.url}}/{{site.baseurl}}/about){% endraw %}
```
Paths to files should also be referenced with the `site.url` and `site.baseurl` variables (see the section on **Adding Images**).

---
---

### Adding Images
*In the examples below, if your image ends with `.png` or `.JPEG`, use the appropriate extension instead of `.jpg`.*  

Images for the blog will generally but put into the `assets/img` folder.  (You can also create a subfolder for images, but you will need to include the subfolder name in the reference link.) 

Markdown syntax for including images is `![Fig Name](path/to/image)`.  For example:
```
{% raw %}![Figure]({{site.url}}/{{site.baseurl}}/assets/img/image_name.jpg){% endraw %}
```
![Figure]({{site.url}}/{{site.baseurl}}/assets/img/image5.jpg)

---
---

### Resizing images

The image I added in the previous section seems a bit large for this post.  Unfortunately,
there isn't a good way to resize images with markdown, so if you need to resize an image, use html instead of markdown and specify the width in the style parameter as follows:

```
{% raw %}<img src="{{site.url}}/{{site.baseurl}}/assets/img/image_name.jpg" alt="" style="width:300px;"/>{% endraw %}
```

(Example with width set to 300 pixels)
<img src="{{site.url}}/{{site.baseurl}}/assets/img/image5.jpg" alt="" style="width:300px;"/>


(Example with width set to 100 pixels)
<img src="{{site.url}}/{{site.baseurl}}/assets/img/image5.jpg" alt="" style="width:100px;"/>




---

### Troubleshooting

Here are some things to keep in mind if your blog appearance isn't going as you planned:

**Problem:  The blog post that I created isn't appearing**

Possible Solutions: 
  - Check your date. GitHub pages won't display blog posts with future dates
  - Check the name of the post file.  It must be in the form "YYYY-MM-DD-title.md".  Make sure that you included the `.md` extension 
  - Check the yaml header.  If there are any special characters in any of the fields, you need to use quotes around the entire field entry.  The most common culprit is the description.  If you're having trouble, try putting quotes around the entire description

---

**Problem:  I know that I made changes to a blog post but the changes aren't appearing**

Possible Solution:
  - Check the header.  If there are any special characters in any of the fields, you need to use quotes around the entire field entry.  The most common culprit is the description.  If you're having trouble, try putting quotes around the entire description.

---

**Problem:  My entire blog has weird formatting**

Possible Solution:
  - Usually this is an address problem.  Double check your url and baseurl in the `_config` file
