# tec-POV


https://easyeda.com/editor#id=f97502b5f0dc4333beb1626a0fecb156
![](https://github.com/SteveJustin1963/tec-POV/blob/master/pics/Schematic_tec-POV_2021-07-20_page-0001.jpg)
![](https://github.com/SteveJustin1963/tec-POV/blob/master/pics/PCB_PCB_tec-POV_2021-07-20_page-0001.jpg)
![](https://github.com/SteveJustin1963/tec-POV/blob/master/pics/Photo%20View_2021-07-20.svg)


## code-1.c
example of C code that you can use to drive the rotating LED bar using two shift registers (74LS595) from a Z80 single-board computer (SBC). This code assumes that you have the necessary hardware connections set up and have the appropriate libraries or drivers installed for the Z80 SBC.

## code-1.z80

The Z80 Assembly code is conceptual and not tested on an actual Z80 system, but a few points could be refined:

1. The delay is only symbolic and won't delay for real milliseconds. To achieve this, you would typically use a timer interrupt, but since that's not specified, the delay loop is just a placeholder.
  
2. `JR` instructions on the Z80 have a limited range of -128 to +127 bytes relative to the address of the instruction immediately following the `JR`. If the code block being jumped over/into is too large, you may run into errors. Replace it with `JP` if needed, which does not have this limitation but consumes more memory and cycles.

3. The ports `#10`, `#11`, and `#12` are placeholders and you'd replace them with whatever actual ports you're using for Data, Clock, and Latch respectively.

4. The loop counter, which is `B` for `PATTERN_LOOP`, gets decremented in `SHIFTOUT_LOOP` as well, but is restored by `POP BC`. This relies on `PUSH BC` before, ensuring `B` is preserved across the call to `SHIFTOUT`. If you edit the program and this chain is broken, it will introduce a bug.

5. The implementation of the `DELAY` routine is very rudimentary. It's a busy-wait loop, which is generally not the best way to implement delays in embedded systems. For precise timing, you'd typically use a hardware timer.

6. The `DELAY` function uses `NOP` to waste time. However, this is very hardware-dependent and might not give you the delay you're expecting. Each `NOP` takes a single machine cycle, but how long a cycle lasts depends on your Z80's clock frequency.

7. Error handling is not included in this example. For a robust implementation, you'd want to include checks for error conditions.

8. Code comments are minimal, and while the code is straightforward, more detailed comments could improve maintainability.

9. Assembly programming can be very hardware-specific. Without knowing your exact setup, it's challenging to write an absolutely correct program.

That said, the code should give a fair idea of how one might go about translating your original C code to Z80 assembly. Make sure to test thoroughly and adapt as necessary for your hardware.
 


## References
- https://en.wikipedia.org/wiki/Persistence_of_vision
- https://www.instructables.com/Rotating-LED-Display-That-Shows-Infinite-Words-POV/
- https://letsmakeprojects.com/make-pov-display-using-arduino-or-rotating-led-display-in-easy-way/

### Iterate
https://github.com/SteveJustin1963/tec-Vectrex

