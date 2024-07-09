## 1. Blinky

The classic, the helloWorld of embedded programming. This program turns the LED on and off periodically.

### Initial steps: 
- Create new project with project generator.
- Open the project folder in VSCode.
- Build the project by pressing the `build` button at the bottom and select the option with `arm-none-eabi`.
- Then, build target can be changed to just the project name, as seen below.
- Make sure the build exits with code 0.

<img src="https://c.l3n.co/i/OW219o.png" width="300">

### Basic Code:

``` C
int main()
{
    stdio_init_all();

    const uint OnBoardLED = PICO_DEFAULT_LED_PIN;
    gpio_init(OnBoardLED);
    gpio_set_dir(OnBoardLED, GPIO_OUT);
    while (true){
        gpio_put(OnBoardLED, true);
        sleep_ms(500);
        gpio_put(OnBoardLED, false);
        sleep_ms(500);
    }
}
```

#### Explanation:
`stdio_init_all()`: initialize stuff

`OnBoardLED = PICO_DEFAULT_LED_PIN`: Get the GPIO number of onboard LED. Remember this is GPIO Number, NOT PIN NUMBER.

`gpio_init(OnBoardLED)`: Initialize that GPIO pin.

`gpio_set_dir(OnBoardLED, GPIO_OUT)`: Set GPIO direction (`GPIO_OUT` for writing and `GPIO_IN` for reading).

`while (true){}`: Super loop of the program

`gpio_put(OnBoardLED, true)`: Set `OnBoardLED` pin to `on` (`true` to turn on/set to high/voltage to VDD, `false` to turn off/set to low/voltage to GND)

Pico logic HIGH voltage is 3.3v and LOW voltage is 0v.

`sleep_ms(500)`: sleep for 500ms.


## 2. Blinky on Other GPIO

Digital output can be tested on other GPIO ports using an LED and a resistor, in this case, connected to GPIO 15.

Resistor has to be used to limit the current overflow. Not using a resistor can lead to the LED getting damaged.


``` C
int main()
{
    stdio_init_all();

    const uint externalLED = 15;
    gpio_init(externalLED);
    gpio_set_dir(externalLED, GPIO_OUT);
    while (true){
        gpio_put(externalLED, true);
        sleep_ms(500);
        gpio_put(externalLED, false);
        sleep_ms(500);
    }
}
```

Do note that `15` is `GP15`, which is the same as `PIN20`, located at the bottom left of the board.

## 3. Pull Up and Pull Down Modes

Digital output mode supports setting different internal pull up and pull down modes. Pull up mode ensures the pin to stay at logic HIGH when nothing is connected to that pin. Same goes for pull down mode, it ensures the pin to stay at logic LOW when nothing is connected. [More info can be found in EEPower's blog](https://eepower.com/resistor-guide/resistor-applications/pull-up-resistor-pull-down-resistor).

Pull up and down resistors internal to the RP2040 IC vary in value between 50kΩ and 80kΩ [as stated in RP2040 Datasheet, table 625](https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf). *need to add why it varies*

 *Add more details*

## 4. Drive Strengths

Current limit can be changed for additional protection against momentary or sustained current spikes. Current limit defaults to 4mA [as stated in section 2.19.4 Pads](https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf)

*Add more details*

## 5. Loading Indicator using LEDs

Control multiple LEDs on multiple GPIOs to show bouncing led. This project configures 5 GPIO ports as digital out and set them to a 4mA drive strength.

*Add more details*

## 6. 5 Bit Binary Counter

Implementing a visual 5 bit counter using the 5 leds from 5.