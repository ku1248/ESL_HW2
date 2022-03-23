github : https://github.com/ku1248/ESL_HW2

General description or introduction of the problem and your solution ：<br>
&emsp;This homework required us to connect the Gaussian blur and testbench modules through TLM bus. In Lab 4 we have practiced how to implement the connection between sobel filter and testbench through TLM bus. Since the overall TLM bus architecture is the same, we have to change the SobelFilter to GaussianFilter in order to perform Gaussian blur to the image.<br>
<br>
Implementation details (data structure, flows and algorithms) :<br>
&emsp;We first implement a bus with one initiator and one target socket. The target socket of TLM bus is connected to the initiator socket on testbench. The initiator socket on testbench is connected to target socket t_skt[0] and t_skt[0] is the first target socket on the TLM bus. And the initiator socket i_skt[0] on the bus is connected to GaussianFilter, also, i_skt[0] is the first initiator on the bus. By setDecode function, we can decode the address given to the bus and since we have set GAUSIAN_MM_BASE as 0x90000000 and set the address to port ID 0 of the bus. The target can get the address that subtracted the GAUSIAN_MM_BASE which is the local address of GaussianFilter and perform specific function. Thus we can send write data or read data from testbench through the bus to the GaussianFilter. <br>
<br>
Additional features of your design and models :<br>
&emsp;In Lab 4, we learned the implementation of sobel filter with TLM bus interconnection. And in this homework, I changed the sobel filter to gaussian filter. I changed the original SobelFilter to GaussianFilter by changing the kernel for convolution and the calculation method. Besides, SobelFilter only needs to send the data of a grey-scaled pixel back to testbench but GaussianFilter needs to send the data of RGB back to testbench. Thus, I added two additional FIFOs, three FIFOs in total to send the data of RGB, each RGB is a char.<br>
<br>
&emsp;Experimental results (on different benchmarks and settings) :<br>
The Gaussian blur filter works correctly since the result image comparing to original image is blurred. Also, the TLM bus works well on the interconnection between testbench and GaussianFilter.<br>
<br>
Discussions and conclusions :<br>
&emsp;The connection from TLM bus to testbench and to GaussianFilter is the key point of this homework. We need to setup the connection between the initiator on the testbench and the target on the bus, and the connection between the initiator on the bus and the target on GaussianFilter. Also, the address mapping is important. Address mapping allow us to setup which port ID we are using to read or write data. We can change the global address to local address by TLM bus to choose which function we want to do and thus read or write the correct data. 
