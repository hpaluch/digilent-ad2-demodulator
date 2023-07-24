# AM Demodulator using Digilent AD2

Here is tutorial - Amplitude Modulation (AM) Demodulator using
`Digilent Analog Discovery 2` Scope/Generator.

NOTE: For learning purpose we use very low and audible frequencies:

* Carrier frequency: 1 kHz
* Envelope frequency: 100 Hz

Real Medium Wave (MW) radio uses 1 MHz band for Radio Frequency (RF)
wireless transmit and Audio signal up to around 4 kHz as Envelope.

However principle is same.

![Digilent AD2 Demodulator](assets/digilent-ad2-scope.png)

Required hardware

* [Digilent Analog Discovery 2](https://digilent.com/reference/test-and-measurement/analog-discovery-2/start)

Required Software

* [Digilent WaveForms](https://digilent.com/reference/software/waveforms/waveforms-3/start)

  - tested version: 3.18.1

Required wiring:

| Pin A | Pin B |
| --- | --- |
| GND | CH1- |
| GND | CH2- |
| W1  | CH1+ |
| W2  | CH2+ |

NOTE: The CH2/W2 wirings are required for later Direct Conversion Example.

# How to run - demodulator using "diode detector"

* Interconnect channels as described in above "Required wiring" table.
* Open provided `Digilent WaveForms`
  Workspace file [Henryk-AM.dwf3work](Henryk-AM.dwf3work)
* Select `Wavegen 1` Tab
* check-on `Enable`
* click on `Run` (or `Run All`)
* It should look like:

![AD2 Demodulator - Generator](assets/digilent-ad2-generator.png)

* select tab `Scope 1`
* click on `Single` for single trigger
* it should look like:

![Digilent AD2 Demodulator](assets/digilent-ad2-scope.png)

You will see 5 channels:

1. Yellow: Sine Carrier at frequency 1 kHz modulated with another
   Sine Envelope (transmitted information) at frequency 100 Hz

2. Red: Demodulated signal - emulating single Diode detector - only positive
   values passes through. This step is fundamental in demodulation,
   otherwise envelope will cancel-out (average is 0) and is base
   for crystal radio. Another popular demodulator
   is Direct Conversion, by mixing Oscillator with same frequency
   as Carrier - see section below for example.

3. Blue: Finally we will filter-out carrier frequency to get just envelope.
   In case of crystal radio, RC low-pass filter is often used. Please
   note that it is always trade-off - to filter out all carrier but
   do not smooth also Envelope - it is usual compromise.

4. Magenta compared to 2. Red -  we demodulate signal using two-way detector (basically
   two diodes so both waves will be used).

5. Green: low-pass filter from Magenta - two-way detector. Notice 2 times higher
   amplitude than in case of single way rectifier (Red) which is handy.

# Direct Conversion Example

Another way to demodulate signal is called "Direct Conversion" - when you mix original input
AM signal (carrier modulated with envelope). If we mix again carrier with oscillator of 
same frequency and phase as carrier we will get back original envelope (there will be also
additional high-frequency result that has to be filtered out).

Here is screenshot of Direct Conversion demodulator - note that this kind of Demodulator
is called "Lock-In" in WaveForms software:

![Digilent AD2 Demodulator - Direct Conversion](assets/digilent-ad2-scope-dc.png)

Here is Wavegen generator tab:

![AD2 Demodulator - Direct Conversion - Generators](assets/digilent-ad2-generator-dc.png)

What we can see:

1. Yellow: Wavegen1: AM Modulated signal - carrier modulated with envelope
2. Blue: Wavegen2: Carrier only - must match carrier from modulated signal
3. Red: Demodulated signal using "Lock-In" scope module.

Here is WaveForms Workspace file for Direct Conversion example:

- Workspace file [Henryk-AM-DC.dwf3work](Henryk-AM-DC.dwf3work)

It is simply amazing how we can easily simulate sophisticated Hardware with such USB Tool!


