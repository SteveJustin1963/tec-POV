# tec-POV


https://easyeda.com/editor#id=f97502b5f0dc4333beb1626a0fecb156
![](https://github.com/SteveJustin1963/tec-POV/blob/master/pics/Schematic_tec-POV_2021-07-20_page-0001.jpg)
![](https://github.com/SteveJustin1963/tec-POV/blob/master/pics/PCB_PCB_tec-POV_2021-07-20_page-0001.jpg)
![](https://github.com/SteveJustin1963/tec-POV/blob/master/pics/Photo%20View_2021-07-20.svg)


## code

 example of C code that you can use to drive the rotating LED bar using two shift registers (74LS595) from a Z80 single-board computer (SBC). This code assumes that you have the necessary hardware connections set up and have the appropriate libraries or drivers installed for the Z80 SBC.

```c
#include <stdint.h>
#include <stdbool.h>

// Define the pins connected to the shift registers
#define DATA_PIN  0x01  // Example pin number for data (D0)
#define CLOCK_PIN 0x02  // Example pin number for clock (D1)
#define LATCH_PIN 0x03  // Example pin number for latch (D2)

// Define the number of LEDs in the bar
#define NUM_LEDS  16

// Define the delay between rotations (in milliseconds)
#define ROTATION_DELAY 12  // Adjust as per your requirements

// Function to shift out the data to the shift registers
void shiftOut(uint8_t dataPin, uint8_t clockPin, uint8_t latchPin, uint8_t data)
{
    for (uint8_t i = 0; i < 8; i++) {
        // Send each bit of data starting from the most significant bit
        bool bit = (data >> (7 - i)) & 1;

        // Set the data pin to the appropriate value (HIGH or LOW)
        // based on the current bit
        if (bit) {
            // Example code assuming you have a function to set a pin HIGH
            setPinHigh(dataPin);
        } else {
            // Example code assuming you have a function to set a pin LOW
            setPinLow(dataPin);
        }

        // Generate a clock pulse to shift the bit into the shift register
        // Example code assuming you have a function to generate a clock pulse
        generateClockPulse(clockPin);
    }

    // Generate a latch pulse to update the output of the shift register
    // Example code assuming you have a function to generate a latch pulse
    generateLatchPulse(latchPin);
}

int main()
{
    // Initialize the shift registers
    // Example code assuming you have a function to set the pins as OUTPUT
    setPinOutput(DATA_PIN);
    setPinOutput(CLOCK_PIN);
    setPinOutput(LATCH_PIN);

    // Character or image pattern data
    uint8_t pattern[] = {0x0F, 0x0E, 0x0C, 0x08, 0x00};  // Example pattern

    // Calculate the delay between steps based on rotation speed (RPM)
    // and the number of steps per revolution
    uint16_t stepDelay = (60000 / (50 * NUM_LEDS));

    // Main loop
    while (true) {
        // Iterate over each pattern element
        for (uint8_t i = 0; i < sizeof(pattern) / sizeof(pattern[0]); i++) {
            // Shift out the pattern data to the shift registers
            shiftOut(DATA_PIN, CLOCK_PIN, LATCH_PIN, pattern[i]);

            // Delay between steps
            // Example code assuming you have a function to delay in milliseconds
            delayMilliseconds(stepDelay);
        }
    }

    return 0;
}
```

Please note that this code is meant to serve as a starting point and assumes that you have the necessary functions or libraries for interacting with the hardware. You may need to modify the code based on your specific setup and requirements.

 C code is ok from a syntactic point of view, but there might be logical errors, mostly depending on the details of  hardware setup and the specifics of the functions used  that are not provided in the code snippet (like `setPinOutput`, `setPinHigh`, `setPinLow`, `generateClockPulse`, `generateLatchPulse`, and `delayMilliseconds`). 

Here are some key points to check:
1. **Pin numbers and functionality**: Make sure the `DATA_PIN`, `CLOCK_PIN`, and `LATCH_PIN` are correctly assigned according to your hardware setup. 
2. **Hardware initialization**: Check that `setPinOutput` is correctly setting the mentioned pins to work as outputs.
3. **Data shifting**: Make sure that the `shiftOut` function is correctly transmitting the bits to the shift register, and that the order is correct (most significant bit first).
4. **Clock and latch pulse generation**: Make sure `generateClockPulse` and `generateLatchPulse` are correctly generating the clock and latch pulses. You'll usually need to set the pin high, then delay a short period, and then set the pin low again to generate a pulse.
5. **Delay function**: The `delayMilliseconds` function should accurately delay the program for the given amount of milliseconds. If the delay is too short or too long, the LED rotation may appear too fast or too slow.
6. **LED pattern**: The `pattern` array should contain the correct bit pattern for the LEDs. Each bit in the array elements corresponds to one LED, and the value of the bit (0 or 1) determines whether that LED is off or on.


## References
- https://en.wikipedia.org/wiki/Persistence_of_vision
- https://www.instructables.com/Rotating-LED-Display-That-Shows-Infinite-Words-POV/
- https://letsmakeprojects.com/make-pov-display-using-arduino-or-rotating-led-display-in-easy-way/

### Iterate
https://github.com/SteveJustin1963/tec-Vectrex

