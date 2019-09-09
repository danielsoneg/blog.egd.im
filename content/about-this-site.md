Title: About this Site
Date: 2019-09-08
Summary: The hardware, software, design, and philosophy powering this site.

I'm taking time now to explore and think about the world, and I wanted a place to write and share what I'm doing. A normal person would get a Medium account and call it a day, but I've got a lot of time on my hands, so I took the chance to experiment and see if I could make something interesting. 

Philosophy
----------
One of the areas I'm interested in right now is how to get to a more decentralized, read/write web. When I started thinking about this project, the idea of not just self-hosting, but hosting from my house really appealed to me. I was particularly inspired by [Low Tech Magazine's solar powered site](https://solar.lowtechmagazine.com/about.html), and a lot of this site's design is informed by theirs. Following that, low power consumption became a big aspect of this site's design, and I'm hoping to go solar soon.

Hardware
--------
This blog is hosted on a [Raspberry Pi Zero W](https://www.adafruit.com/product/3400) sitting in my living room. I'm lucky enough to have [Sonic's](https://www.sonic.com/) symmetric gigabit fiber service, which should carry me until I'm a lot more popular than I am now. I've got the Pi connected wirelessly - my goal is to get it wired up to a solar panel and battery and have it live on my deck. The Pi draws ~.3W idle and around ~.8W under as much load as I can throw at it (it's not, to be clear, fast), so even given that we're going into winter, I think this is tractable. It's really a pretty amazing little device - I'm blown away that I've got a full-fledged computer hosting this site for $10.

Software
--------
Both to keep the power budget low and to keep the site simple, I decided to use a static site generator so the only thing the Pi needs to do is serve HTML. On the Pi side, it's basically just Nginx serving HTML. Like a [good web citizen](https://www.eff.org/encrypt-the-web), I'm using LetsEncrypt for SSL, which seems to have minimal power impact and was dead simple to set up - there's a plugin now for Nginx which makes it effectively a one-click affair. The only other thing running on the Pi is a cron job that updates my DNS entries on Gandi - Sonic unfortunately doesn't offer static IPs, but Gandi offers an API for DNS.

The content generator I'm using is [Pelican](https://blog.getpelican.com/). I chose Pelican over Jekyll or any of the others because I'm most comfortable with Python - being able to crack it open and look at the source code was a big help during the development process. Pelican's easy enough to work with, and everything is Markdown and Jinja templates, so when I inevitably forget how any of this works (looking at you, my nine other previous blogs), I can at least port the content and templates pretty easily.

Design
------
For the site design, I had three targets I was optimizing for - simplicity, readability, and accessibility.

I wanted simplicity for two reasons. First, [the web is full of bullshit these days](https://twitter.com/darylginn/status/1053646859686809600). Second, the site's power budget is partly philosophical, and I wanted to make sure I wasn't just offloading my footprint onto my readers. There's no Javascript in use anywhere on this site, no fonts that aren't standard, and some fairly simple CSS.

Most of the CSS in use is designed to promote readability. The primary purpose of this site is long-form writing, so the site design is intended to improve readability. Wherever I could find reasonable consensus on aspects of article design for readability, I followed it: line width is around 70 characters, line spacing around 1.5x, left-aligned text, serif font. The whole design is flexible, so it'll zoom nicely. The site also supports "dark mode," and Safari, Chrome, and any other browser that properly supports the ["prefers-color-scheme"](https://caniuse.com/#feat=prefers-color-scheme) query.

Finally, I wanted to make the site as accessible as possible. I think this is both the kind thing to do and a human imperative. In that light, the site makes extensive use of semantic tags (correctly, I think), uses high contrast ratios, and generally is built to be legible to both machines and humans.

Conclusion
----------
I'm really happy with how this project has turned out so far. It feels like something from an earlier web - I'm hosting static HTML content on a server in my living room. There's no tracking cookies, no expensive scripts, and a relatively short load time overall. At the same time, it's leveraging a lot of new development: I've got gigabit fiber to my home, which means I can do this without worrying about bandwidth; the Raspberry Pi costs a whopping $10 and costs practically nothing in energy; I've got a free, valid SSL cert; and the tooling to set all this up was easy to use and easy to set up.