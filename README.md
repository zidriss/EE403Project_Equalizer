EE403Project_Equalizer
This repository is to show the code that my group and I used to realize our graphical equalizer for our senior design class here at Penn State. 

The software used was the Keil uvision program using the language C. 
The graphical libarary, eGFX, was used to draw both the sliders and the equazlier bands. The source code called main.c is up on the server. This basically shows the architecture of the software. The project itself had many more scripts, linking perhical to memory locations and using the CMSIS DAP math libraries. 

This project used the BiQuad filter, to proudce a 5 band equazlizer. Each band is centered around a center frequency, 250Hz, 500Hz, 1kHz, 2kHz, and 4kHz. Adding more bands, or changing the center frequency is only a question of recreating or chaning current code (seen in main.c). Each band is controlled using a slider, and so the outout signal can be parsed to have only lows, mids, highs, or any combination thereof. 

The audio input occurs via an aux CODEC board on the LPCXpresso54608 board. 

If you have any questions, feel free to messege me and I'll do my best to answer them. 
