# pxt-cozir
# COZIR sensor by Let's Talk Science
This library provides category blocks to collect data from the custom MonkMakes GSS COZIR printed circuit board sensor.

This project was made possible through the generosity of our supporters, the government of Canada CanCode initiative and the Canadian Space Agency.

## License
MIT License
Copyright 2018 Let's Talk Science
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Code of Conduct
This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Supported targets
* for PXT/microbit



## Calibrate COZIR with Altitude in SetUp
English Link: https://makecode.microbit.org/_0AxRHuahWRJd 

```blocks
let modes: string[] = []
let mode = 0
input.onButtonPressed(Button.A, function () {
    mode += 1
    if (mode == 3) {
        mode = 0
    }
    basic.showString(modes[mode])
})
input.onButtonPressed(Button.B, function () {
    COZIR.calibrateCo2()
    basic.showString("+")
    basic.pause(500)
})
input.onButtonPressed(Button.AB, function () {
    COZIR.setAltitude(1159)
    COZIR.setupCozir()
    basic.showString("x")
    basic.pause(500)
})
serial.redirect(
SerialPin.P0,
SerialPin.P1,
BaudRate.BaudRate9600
)
mode = 0
modes = [" PPM", " C", " %RH"]
basic.showIcon(IconNames.Yes)
basic.pause(3000)
basic.showIcon(IconNames.Happy)
basic.forever(function () {
    basic.showString(modes[mode])
    if (mode == 0) {
        basic.showNumber(Math.round(COZIR.Co2()))
    }
    if (mode == 1) {
        basic.showNumber(Math.round(COZIR.temperature()))
    }
    if (mode == 2) {
        basic.showNumber(Math.round(COZIR.relativeHumidity()))
    }
})
```

French Link: https://makecode.microbit.org/_FCW38vX0c9p4 


### Calibrate COZIR with Altitude in SetUp
