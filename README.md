EE403Project_Equalizer
This repository is to show the code that my group and I used to realize our graphical equalizer for our senior design class here at Penn State. 

The software used was the Keil uvision program using the language C. 
The graphical libarary, eGFX, was used to draw both the sliders and the equazlier bands. The source code called main.c is up on the server. This basically shows the architecture of the software. The project itself had many more scripts, linking perhical to memory locations and using the CMSIS DAP math libraries. 

This project used the BiQuad filter, to proudce a 5 band equazlizer. Each band is centered around a center frequency, 250Hz, 500Hz, 1kHz, 2kHz, and 4kHz. Adding more bands, or changing the center frequency is only a question of recreating or chaning current code (seen in main.c). Each band is controlled using a slider, and so the outout signal can be parsed to have only lows, mids, highs, or any combination thereof. 

The audio input occurs via an aux CODEC board on the LPCXpresso54608 board. 

The signal is parsed into two 16 bit channels, each of which are individually computed upon using the BiQuad filter (an IIR filter) 
the BiQuad filter has both feed forward and feed backward coefficients which are summed – so the feed backwards are initially set to zero
The BiQuad type filter we chose to use for all bands was a band pass filter centered upon the previously mentioned frequencies
Coefficients used to compute are based on the cookbook
Each band has a different set of coefficients.
The signal is split using a parallel BiQuad structure
Where each band had 2 filters, for a right and left channel
The resulting signal, is then summed up and the left channel is bit shifted 16 bits to output to the outgoing audio CODEC
Each band is displayed using the RMS value over 1024 samples
Where an array of RMS’s values are then plotted for each band using the eGFX functions

To create a coherent coding structure, as each band has different coefficients, multiple type defined structures where initialized
This created a variable types for both the coefficients, and states
Variables are then set up of the type defined structures, they are then passed to the BiQuad function (all this code is in main).
The coefficients computation and the BiQuad filter use the same variables of the type defined structures
The coefficient computation function and BiQuad filter are both functions
BiQaud filter in in the interrupt to compute in real time, but the coefficients and state initialized in the that main function (not a loop) as they are static variable


If you have any questions, feel free to messege me and I'll do my best to answer them. 
