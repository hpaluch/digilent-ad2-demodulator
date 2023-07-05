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

NOTE: The CH2/W2 wirings are optional (reserved for future experiments).

# How to run

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

You will see three channels:

1. Sine Carrier at frequency 1 kHz modulated with another
   Sine Envelope (transmitted information) at frequency 100 Hz

2. Demodulated signal - emulating Diode detector - only positive
   values passes through. This step is fundamental in demodulation,
   otherwise envelope will cancel-out (average is 0) and is base
   for crystal radio. Another popular demodulator
   is Direct Conversion, by mixing Oscillator with same frequency
   as Carrier, but it is not shown in this example.

3. Finally we will filter-out carrier frequency to get just envelope.
   In case of crystal radio, RC low-pass filter is often used. Please
   note that it is always trade-off - to filter out all carrier but
   do not smooth also Envelope - it is usual compromise.




