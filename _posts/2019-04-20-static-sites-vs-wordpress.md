---
category: Web Dev
tags:
- Wordpress
- Static Sites
- CMS
background: Default
title: Static Sites vs Wordpress
background_color: ''
background_image: ''
background_glsl: ''
date: 2019-04-20 18:53:32 +0000
layout: post
---
## "Is a Static Site Right for Me?"

#### Probably! Unless your website needs to be _really_ complicated

- Zero maintenance
- Unhackable
- Lightning fast

...there are lots of reasons to love static websites. If you've dealt with hosting a website in the last decade, some of the things you just read probably made your eyes light up. If not, let me paint a picture by comparing static sites to the most common approach, powering 1/3rd of the websites online today: Wordpress.

### What's wrong with Wordpress?

Wordpress is an incredibly powerful CMS, but with great power comes great overhead. I've spent more time working on Wordpress sites than any other platform, and I recommend it often, but the truth is it's not right for every site. So what are some of the issues that come up when you use a powerful CMS like Wordpress, Joomla, or Drupal?

- Maintenance: 
    - It's not uncommon for a Wordpress site to have a dozen or more plugins, and each of those plugins might update once a year or five times a month. If you don't update these plugins, you risk security vulnerabilities and outdated techniques; if you do update you run the risk of new incompatibilities breaking your site.
    - Static sites are just html files, images, and other assets stored in the cloud. If you host a static site with me and you stop paying for it, it'll just stay there, loading flawlessly, for as long as I can assure it and as long as the domain name is paid for.
- Security:
    - With great power comes great responsibility. Wordpress and other standard hosting solutions have so much capability that a compromised site can be turned into a proxy node for hacker operations, a spam email server, or an endless list of porn links. Seriously, I have no idea why they do that, but I've seen it happen - more than once. 
    - The static sites I host are <a href="https://github.com/security" target="blank">effectively unhackable.</a>
- Cost:
    - Let's start with the cheapest hosting you can find, for $3 a month: $36/year
    - Godaddy's SSL certificate for $80 a year: we're at $116/year
    - A bare minimum of $50 twice a year to have someone check on your site security: $166/year so far
    - A few hundred every year or two to fix a vulnerablity or broken upgrade... this is getting costly
- Speed:
    - Every time you load a Wordpress page, it sends a request to a server computer that dynamically processes the request and returns a webpage. This is incredibly powerful... and incredibly slow.
    - With static sites, everything is rendered any time you make an update in the admin panel. This means nobody will ever <a href="https://blog.kissmetrics.com/wp-content/uploads/2011/04/loading-time.pdf" target="_blank">abandon your site waiting for it to load</a>.

In a nutshell, by building your whole website ahead of time instead of building each page every time someone visits your site you take away all maintenance and security concerns, and reduce your ongoing costs and page load times to the lowest possible. 

This website is static and it's:
- Maintenance Free
- Unhackable (go ahead, try me)
- Costs me about $8 a year
- Loads in less than 0.5 seconds
