# tec-POV


https://easyeda.com/editor#id=f97502b5f0dc4333beb1626a0fecb156
![](https://github.com/SteveJustin1963/tec-POV/blob/master/pics/Schematic_tec-POV_2021-07-20_page-0001.jpg)
![](https://github.com/SteveJustin1963/tec-POV/blob/master/pics/PCB_PCB_tec-POV_2021-07-20_page-0001.jpg)
![](https://github.com/SteveJustin1963/tec-POV/blob/master/pics/Photo%20View_2021-07-20.svg)


## code
- code-1.c
 example of C code that you can use to drive the rotating LED bar using two shift registers (74LS595) from a Z80 single-board computer (SBC). This code assumes that you have the necessary hardware connections set up and have the appropriate libraries or drivers installed for the Z80 SBC.



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

