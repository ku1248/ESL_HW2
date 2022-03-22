github : https://github.com/ku1248/ESL_HW2

General description or introduction of the problem and your solution ：<br>
&emsp;This homework required us to connect the Gaussian blur and testbench modules through TLM bus. In Lab 4 we have practiced how to implement the connection between sobel filter and testbench through TLM bus. Since the overall TLM bus architecture is the same, we have to change the SobelFilter to GaussianFilter in order to perform Gaussian blur to the image.<br>
<br>
Implementation details (data structure, flows and algorithms) :<br>
&emsp;We first implement a bus with one initiator and one target socket. The target socket of TLM bus is connected to the initiator socket on testbench. The initiator socket on testbench is connected to target socket t_skt[0] and t_skt[0] is the first target socket on the TLM bus.

Additional features of your design and models :
  I changed the sobel filter in Lab 2 into Gaussian blur filter. Since the result of Gaussian blur filter is not grey scale. I added some new FIFOs to transfer the result of Gaussian blur for R, G, and B. And also, I used row buffer to save row pixels to prevent sending or receiving the same data repeatly.

Experimental results (on different benchmarks and settings) :
  The Gaussian blur filter works correctly since the result image comparing to original image is blurred. However, in order to implement it in row-based fashion, I spend additional cycles to send pixel row data into buffers. So the simulated time (720642 ns) compared to sobel filter (655358 ns) is longer but we saved the data transfer of repeated data.

Discussions and conclusions :
  Since homework 1 and Lab 2 are both implementing filter to image, so I discuss them together. In Lab 2, for each 9 cycles, Testbench receive and send 9 pixel of data into FIFOs. But for the 9 pixels sent, the 6 pixels of them are same as the pixels that we have received and sent already. So, in homework 1, I send the pixels of a row into buffers and send them into FIFOs in order. The advantage of this method is to prevent receiving the same pixel data repeatly. The pixel transfered in Lab 2 is about 9 * 256 * 256, however, in homework 1, using row-based fashion, the pixel transfered is just 256 * 256. The conclusion is that in this homework, I saved the data transfer about (1 / 9) although I may spend some additional time reading row pixel data.
