# BeagleBone-IO

Firmata-compatible BeagleBone Black device API

Heavily based on [Galileo-IO](https://github.com/rwaldron/galileo-io) by [Rick Waldron](https://github.com/rwaldron)

## Install

```
$ npm install beaglebone-io
```

## Usage

``` js
var BeagleBone = require('beaglebone-io');
var board = new BeagleBone();

board.on('ready', function () {
  this.digitalWrite(13, this.HIGH);
  this.analogRead('A0', function () {
    console.log(this.value);
  });
});

```

With Johnny-Five
``` js
var five = require('johnny-five');
var BeagleBone = require('beaglebone-io');

var board = new five.Board({ 
  io: new BeagleBone()
});

board.on('ready', function () {
  var led = new five.Led();
  led.blink();
  
  this.repl.inject({ led: led });
});
```

## Pin Mappings

BeagleBone Black to Arduino UNO

| BBB Port | Arduino Pin | Type |
|----------|-------------|------|
|P8_7|0|Digital|
|P8_8|1|Digital|
|P8_9|2|Digital|
|P8_13|3|PWM|
|P8_10|4|Digital|
|P9_14|5|PWM|
|P9_16|6|PWM|
|P8_11|7|Digital|
|P8_12|8|Digital|
|P9_21|9|PWM|
|P9_22|10|PWM - Currently not working|
|P9_28|11|PWM - Currently not working|
|P8_14|12|Digital|
|USR3|13|Digital / Default Led|
|P9_39|A0|Analog Input|
|P9_40|A1|Analog Input|
|P9_37|A2|Analog Input|
|P9_38|A3|Analog Input|
|P9_35|A5|Analog Input|
|P9_36|A5|Analog Input|

## The MIT License (MIT)

Copyright (c) Julian Duque 2014

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
