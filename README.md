emu2149
=======

A YM2149 (aka PSG) emulator written in C.

# Note for rate conversion

The internal sample rate converter in emu2149 is a light-weight, simplified procedure.
Even if `1` is set to the quality (PSG_setQuality), the alias noise cannot be completely eliminated.

To obtain the best accurate result, an external sample rate conversion should be used. 
Please follow these steps.

1. Set the sample rate to 1/8 of the chip's master clock. i.e. rate=223721Hz for master=1.78MHz.
2. Set `0` to the quality value with `PSG_setQuality(psg, 0)` so that you can bypass the internal rate converter.
3. Call `PSG_calc()` to generate samples.
4. Apply your preferred external rate converter to the samples to obtain your desired sample rate.