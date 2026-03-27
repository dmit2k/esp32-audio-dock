# XIAO PWM + ADKEY Snapshot

This top-level repo currently points to a working `squeezelite-esp32` submodule state.

The verified feature set includes:

- XIAO ESP32-S3 I2S output
- PWM master volume control
- ADC resistor-ladder media buttons

Current GPIO assignments:

- I2S BCLK = GPIO6
- I2S LRCK = GPIO5
- I2S SDATA = GPIO4
- PWM master volume = GPIO9
- ADKEY input = GPIO7

Hardware note:

- An external 18k pull-up to 3.3V was required on ADKEY for this board revision.

Build image used:

- `local/espressif-idf:4.4-pwm`

This branch is a practical working checkpoint, not an upstream-ready feature split.
