Title: About this Site
Date: 2019-09-10
Summary: The hardware, software, design, and philosophy powering this site.

I'm taking time now to explore and think about the world, and I wanted a place to write and share what I'm doing. A normal person would get a Medium account and call it a day, but I've got a lot of time on my hands, so I took the chance to experiment and see if I could make something interesting.

Philosophy
----------
One of the areas I'm interested in right now is how to get to a more decentralized, read/write web. When I started thinking about this project, the idea of not just self-hosting, but hosting from my house really appealed to me. I was particularly inspired by [Low Tech Magazine's solar powered site](https://solar.lowtechmagazine.com/about.html), and a lot of this site's design is informed by theirs. Following that, low power consumption became a big aspect of this site's design, and I'm hoping to go solar soon. I'm also interested in a web that supports learning and sustained attention, and so I wanted to build a site where readers could engage with the content however they wanted.

Hardware
--------
This blog is hosted on a [Raspberry Pi Zero W](https://www.adafruit.com/product/3400) sitting in my living room. I'm lucky enough to have [Sonic's](https://www.sonic.com/) symmetric gigabit fiber service, which should carry me until I'm a lot more popular than I am now. My goal is to get the Pi wired up to a solar panel and battery and have it live on my deck. It draws ~.3W idle and around ~.8W under as much load as I can throw at it (it's not, to be clear, fast), so it's not going to take much to power it year-round. It's really a pretty amazing little device - I'm blown away that I've got a full-fledged computer hosting this site for $10.

Software
--------
I'm using a static site generator, so the only thing the Pi needs to do is serve HTML. It's good for the power budget and helps keep the site simple - on the Pi side, it's basically just Nginx serving HTML. Like a [good web citizen](https://www.eff.org/encrypt-the-web), I'm using LetsEncrypt for SSL. SSL had minimal power impact and certbot was dead simple to set up - there's a plugin now for Nginx which makes it effectively a one-click affair. The only other thing running on the Pi is a cron job that updates my DNS entries on Gandi - Sonic unfortunately doesn't offer static IPs, but Gandi offers an API for DNS.

I'm using [Pelican](https://blog.getpelican.com/) to generate the site. I chose Pelican over Jekyll or any of the others because I'm most comfortable with Python - being able to crack it open and look at the source code was a big help during the development process. Pelican's easy enough to work with, and everything is Markdown and Jinja templates, so when I inevitably forget how any of this works (see: all my previous blogs), I can at least port the content and templates pretty easily.

Design
------
The design took longer than I expected - I always forget how long it takes to build a full site template from scratch. I kept it as simple as possible -  there's no JS anywhere, no non-standard fonts, and no tracking or analytics. The site is geared towards longer-form text, so the design is focused on readability, both on desktop and mobile. Everything is flexible and should scale as needed, and there's a "Dark Mode" for browsers that properly support the ["prefers-color-scheme"](https://caniuse.com/#feat=prefers-color-scheme) query (Chrome & Safari on Mac, at least). Finally, for accessibility, the site uses semantic tags wherever I could figure out that they'd go, and I kept the design as high-contrast and easily visible as I could. Everything should be legible to both machines and humans - there's even an RSS feed.

Conclusion
----------
I'm really happy with how this project turned out. It feels like something from an earlier web - I'm hosting static HTML content on a server in my living room. There's no tracking cookies, no scripts, and a relatively short load time overall. At the same time, I'm serving off a $10 computer that'll be powered by solar pretty soon, which has a very sci-fi feel to me. The whole site's done using modern html and css, built to support screen readers, is using SSL, and is easy to update. I'll be even happier when I've got the solar set up, but I'm proud of how this project turned out.