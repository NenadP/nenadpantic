---
title: Playing with Arduino LCD
date: 2016-02-21 18:03:52
tags: ["Arduino", "Node.js", "IoT"]
---

Saturday evening and I finally found some time to play a bit more with my [Arduino Starter Kit][1] bought around Christmas. Actually I was playing with basic stuff when I bought it, but the connection wires shipped with starter kit are actually not so good for fast prototyping - they are very stiff, so I ordered some [flexible ones][2] - be sure to get yourself these as it will make your Arduino first steps much easier.

I wanted to go with some more complexity this time and went with [LCD Hello World][3] example. There was fairly lot of pins to connect to Arduino, breadboard and LCD,  and that's really fun. if you wear a glasses like me and are farsighted, prepare for some struggle. Good thing, nothing was broken or burnt even when I connected wrong pins. You will need to have **Arduino IDE** to run the examples, which I did - loaded the basic C++ LCD demo. I needed to resolve the issue being unable to upload the demo on Arduino - comm port option (USB really) was greyed out - quick fix was to **run arduino with sudo**.

![Arduino LCD demo][lcd_c].

I wondered if it would be possible to write the Arduino programs with JavaScript. Happily, Google returned some nice results: there is [Johnny Five][4] **Node.js library** for that. Another one I checked was [Cylon.js][5].

The board setup for it seemed different a little bit, so I rewired whole board just in case, trying hard to hit right pins under poor light. But hey, at least is not soldering :) . Eventually it worked, loading the LCD demo. Uploading to Arduino went smoothly, all you need to do is run `node yourProgram.js` and it will do it for you. Again some work was needed to obtain control over comm port though. There are numerous of methods provided by the library, and you can even **define your own characters** (5 x 8), something like:
```javascript
lcd.createChar("duck2", [0, 12, 29, 15, 15, 6, 0]);
lcd.useChar("duck2");
lcd.clear().cursor(0, 0).print(":duck2:");
```
...where array of numbers is of course 8 rows of 5 bits.

So after all that was fun and inspiring, lots of ideas coming to mind, I'll be sure playing with it more in the future; be aware that [Internet of Things][6] might be the next big thing!

![Arduino LCD demo Node.js][lcd_js].

[lcd_c]: /images/arduino_lcd.jpg
[lcd_js]: /images/arduino_lcd_node.jpg
[1]: https://www.arduino.cc/en/Main/ArduinoStarterKit
[2]: http://www.amazon.com/Generic-Solderless-Flexible-Breadboard-Arduino/dp/B00IKBLLUE
[3]: https://www.arduino.cc/en/Tutorial/HelloWorld
[4]: http://johnny-five.io/
[5]: https://cylonjs.com/
[6]: https://en.wikipedia.org/wiki/Internet_of_Things