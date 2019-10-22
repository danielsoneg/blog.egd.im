Title: A Solar Powered Raspberry Pi, Part 1
Date: 2019-10-21
Summary: The basic solar setup for the site, and some plans for the future.

I mentioned in the previous post that, given the low power draw for the Pi Zero, I wanted to build a solar power setup for this site - well, this blog is now powered by the sun:
![A grey plastic box next to a solar panel](/images/solar_pi.jpg "The solar build")

Approach
--------
It's possible to just buy a solar powered battery online, but what's the fun in that? I wanted to actually build and understand the system in the end, so I decided to buy the kit separately. At the same time, this is my first project in a while, and I'm new to solar and not particularly versed in electronics, so I limited myself to sizing, assembling, and some light soldering and craft work for the project. I bought all the pieces from [Adafruit](http://adafruit.com) to make sure everything would work well together. On a scale of 0-10 wrenches, I kept this at a 3 or 4.

Power Requirements
-------------
The first step was getting a good read on the actual power requirements for the Pi. I did some searching online and gave a go at measuring with a kill-a-watt, but I wasn't comfortable building to any of the numbers I was seeing. I bit the bullet and bought a [USB power meter](https://www.amazon.com/gp/product/B078SQ9HRG/) (That's the one I used, but don't take this as a strong endorsement of that product. It worked, end of praise), and performed two tests. First, I let the Pi run for 24hrs under normal conditions - this yielded around 1700mA of draw, a steady ~70mAh. Second, I ran siege against the Pi to see what the peak power draw was. The nice part about the Pi is that it's effectively constrained by the CPU - there's just not that much juice in the tank, so the power draw never gets that high - at peak, the Pi drew 140ma, about double what it was at steady state. That gave me my upper and lower bounds - between 1700 and 3400mA draw per day, although I expect the Pi will wind up overheating and throttling itself if it's run at 100% for that long.

Sizing the components
------------
Sizing the battery was easy enough - I wanted enough power to last at least 3 or 4 days on battery alone. Adafruit's [largest LiIon battery](https://adafru.it/353) is 6600mAh, which is good enough for about 3.5 days (I got a chance to test that later, and it indeed delivers a bit over 3 days of juice). 

The bigger challenge was sizing the solar panel. Solar panel output per day is heavily variable based on location, weather, time of year, orientation, angle, and more. There's a set of calculations I could do to figure out the right size solar panel, but even then, I'd get average output, not accounting for sustained or unseasonably bad weather. After careful consideration, I listened to my inner engineer, punted on the whole problem, and picked up [the biggest panel Adafruit had](https://adafru.it/2747).

It's a 9w/6v panel, so in ideal conditions it'll generate around 1500mA of power, which is almost sufficient to power the Pi for the whole day. Given a minimum 8 hours of useable daylight, even in bad conditions I should be generating enough power to top up the battery enough to keep going. The charging circuit itself is actually limited to 1000mAh, so I'm not getting the peak output from the panel, but my impression is that peak numbers for panels are sort of like peak distance for WiFi.

Everything Else
----------
The other two electronic components involved are a [solar/LiIon charger circuit](https://adafru.it/390) and a [5v power booster](https://adafru.it/2030). The charging circuit is actually one of the limiting factors in the build - it won't supply more than 1000mAh to the battery - but its load circuit is designed to use power from the panel first and only pull from the battery if it's not getting enough juice from the solar panel. The power booster is pretty basic - the only thing I'll note is that I ruined the first one because I hadn't soldered anything in 2 years and forgot how. Oops.

I packed everything into a waterproof container I picked up from a [local electronics shop](http://allashers.com/) and chained it to my deck facing south. A day later, the battery was charged. I plugged in a separate Pi to keep an eye on it, and after a week (and then another one while I was out of town), I swapped out for the Pi powering this blog.

What's next
----------
The biggest issue with the build - and the first thing I'm fixing - is I have no visibility into the battery charge level, the solar panel output level, or the temperature inside the enclosure. I'm pretty sure the panel and battery are oversized for the project, but I'd really like to collect some long-term data on power flow within the system. The Pi has GPIO but no analog inputs, so I'll need to either hack something together or get a proper ADC board to build with. I'm also a bit curious about the added power draw from having the Pi itself check the power levels - the basic rule is the less the Pi does, the better (there's a quantum mechanics joke in here somewhere). Stay tuned for part 2.

I'm also interested in what else I can do to build on the "microgrid" aspect of this project. I've got a nice big patio, so I've got enough room for some larger panels - I'd love to be able to power more of my life from solar, even in an apartment. I'm also looking into helical and vertical wind turbines - I don't think it's any kind of economical, but then again, I won't have to shut it off because I paid dividends instead of maintaining it.

Last thoughts
---------
This was a relatively easy build, but it did its job - I learned a lot about sizing and building solar and battery systems, and I've got some more work to follow that'll be a good next step in learning circuit design. Beyond that, though, it just makes me smile every time I look at it - I love that my blog is running on a tiny computer hooked up to a solar panel. It's inspiring me to look more into microgrid technology, especially following PGE's recent fuckups. If you've got the time, will, and a site you don't actually care that much about, I recommend the build.

Part List
---------
Almost everything was purchased from Adafruit. If you'd like to build one yourself, [I created a wishlist with all the components.](https://www.adafruit.com/wishlists/495232)

From Adafruit:

- [Colossal 6V 9W Solar Panel - 9.0 Watt](https://adafru.it/2747)
- [Lithium Ion Battery Pack - 3.7V 6600mAh](https://adafru.it/353)
- [USB / DC / Solar Lithium Ion/Polymer charger - v2](https://adafru.it/390)
- [10K Precision Epoxy Thermistor](https://adafru.it/372) (shuts off the charging circuit if the battery temperature is too high)
- [3.8/1.3mm or 3.5/1.1mm to 5.5/2.1mm DC Jack Adapter Cable](https://adafru.it/2788) - Connects the solar panel to the charge circuit
- [PowerBoost 1000 Basic - 5V USB Boost @ 1000mA from 1.8V+](https://adafru.it/2030)
- [Raspberry Pi Zero W Basic Pack](https://adafru.it/3409)

From Elsewhere:

- [Waterproof Enclosure from Al Lasher's Electronics](http://allashers.com)
- 2Kohm Resistor from a drawer - Bumps the charge circuit from 500mAh to 1000mAh (I included this in the wishlist above, but I just had it lying around already)

Total Cost: $171.65, including the Pi, not including tax or shipping.