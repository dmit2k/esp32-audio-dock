# XIAO PWM + ADKEY working checkpoint

This repository currently points to a hardware-tested `squeezelite-esp32` submodule state for a XIAO ESP32-S3 based audio control setup.

## What this checkpoint includes

Working features:

- I2S audio output from XIAO ESP32-S3
- PWM-based master volume control for ADAU AUXADC
- ADC resistor-ladder media buttons (ADKEY)

## Current GPIO assignments

- I2S BCLK = GPIO6
- I2S LRCK = GPIO5
- I2S SDATA = GPIO4
- PWM master volume = GPIO9
- ADKEY input = GPIO7

## Hardware notes

This setup is used with an ADAU1466 + SSM3582 based audio system.

Important board-specific note:

- On this board revision, the ADKEY input did not have a working pull-up on the main board.
- A tested external pull-up was required:
  - 18k from 3.3V to ADKEY

Measured ADKEY voltages with the external 18k pull-up:

- idle ≈ 3.2V
- button 1 ≈ 0.46V
- button 2 ≈ 0.84V
- button 3 ≈ 1.0V

## ADKEY button mapping

- button 1 -> PREV
- button 2 -> PLAY/PAUSE
- button 3 -> NEXT

## Build environment

Builds are performed using the local Docker image:

- `local/espressif-idf:4.4-pwm`

Current tested build mode:

- `DEPTH=32`

## Flashing approach

The current workflow flashes only the application image to the OTA app partition:

- `build/squeezelite.bin`
- flash address: `0x150000`

This avoids erasing the whole device and preserves the general OTA-style workflow.

## Purpose of this branch state

This is a practical working checkpoint for the XIAO ESP32-S3 + ADAU1466 hardware setup.

It is not intended to be a clean upstream-ready feature split.
It is intended to preserve a tested combined state with:

- working playback
- working PWM volume control
- working ADKEY media buttons

