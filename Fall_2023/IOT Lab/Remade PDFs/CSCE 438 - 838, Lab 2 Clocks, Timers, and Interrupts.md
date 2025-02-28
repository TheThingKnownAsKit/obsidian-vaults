## Clocks, Timers, and Interrupts
Embedded systems often require mechanisms for counting the occurrence of events and for performing tasks at regular intervals. Two types of hardware are used by microcontrollers to support these functions:
* Clock: A periodic signal with a certain frequency (clock frequency).
* Timer: A counter that is updated based on some type of event, clock signal, or an external event.
By using clocks and timers, we can ensure that events are not missed and that timing of behavior occurs at regular intervals. Hence, it is important to choose the configurations for clocks and timers accordingly to satisfy the requirements.

### Clock System
Almost every embedded board has an oscillator, a circuit whose sole purpose is generating a repetitive signal of some type. Digital clock generators, or simply clocks, are oscillators that generate signals with a square waveform. Basically, the edges of the square waves trigger hardware throughout the device so that the changes in different components are synchronized. Different components may require oscillators that generate signals of various waveforms. For example, sinusoidal, pulsed, sawtooth, and more. In the case of components driven by a digital clock, it is the square waveform. The waveform forms a square because the clock signal is a logical signal that continuously changes from 0 to 1 or 1 to 0. The output of the synchronous sequential circuit is synchronized with that clock.
![Clock signal](https://paper-attachments.dropbox.com/s_982943DEA1A0730A6A5668D6F0CB5E11011C141B01B5F7B38C6969E986EF4D1B_1567966904712_image.png)

