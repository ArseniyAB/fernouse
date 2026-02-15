# fernouse
Gaming mice kinda suck... This one shouldn't. 


## Features
* 1000Hz+ polling rate - If I don't hit 1k, I did something wrong.
* Wireless and Wired USB-C connection
* 13 buttons
    * left-right tilt mouse wheel buttons
    * 4 thumb buttons + 5th button on thumb rest
    * 2 buttons to the side of the left-primary button
    * 1 button behind scroll wheel
    * 1 button on scroll wheel
* Magnetic-sense scroll wheel
* 400mAh battery for ~10h operation (TBD)
* Weight: As close to 100g as I can get it (TBD)
* Extra buttons Mapped to keyboard characters (cuz some games still have    trouble with extra mouse buttons)


## Critical Hardware
* Main Chip on mouse: nRF52840
* Main buttons:  Omron D2FC-F-7N(60M)
* Auxilary buttons: omron D3C-1220
* Sensor: PAW3395 
* Mangetic Sensor: TMAG6180 (analog sine/cosine)
* USB-C connector
* Dongle: NRF52840 MDK USB DONGLE (literally easiest decision of my life)
    ### For maximum polling rate
    * Change dongle to a STM32H753ZI Nucleo-144 STM32H7 ARM® Cortex®-M7 MCU 32-Bit Embedded Evaluation Board
        for faster USB polling speeds (STM32 supports HighSpeed USB)
    * Attach the original NRF52 dongle to the STM as a simple receiver
* Small magnet to place inside of the mouse wheel



## Signal Filtering
* It would make sense to at least leave space for a low pass filter for the sinusoidal outputs of the magnetic field sensor. 
    This may even be required for the same reason mentioned in the next point, we're already doing ArcTan calcs 

* Debounce all buttons with a small cap <- Hoping not to have to debounce in software increasing delay

* 