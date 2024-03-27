## Blinky

The classic, the helloWorld of embedded programming. This program turns the LED on and off periodically.

### Initial steps: 
- Create new project with project generator.
- Open the project folder in VSCode.
- Build the project by pressing the `build` button at the bottom and select the option with `arm-none-eabi`.
- Make sure the build exits with code 0.

<img src="https://a.l3n.co/i/O82htM.png" width="300">

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

---

