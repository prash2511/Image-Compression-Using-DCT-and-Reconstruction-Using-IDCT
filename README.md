# Digital Image Compression using DCT & Reconstruction using IDCT


* Need for Image Compression -
1) Image compression is minimizing the size in bytes of a graphics file without degrading the quality of the image to an unacceptable level. 

2) The reduction in file size allows more images to be stored in a given amount of disk or memory space. 

3) It also reduces the time required for images to be sent over the Internet or downloaded from Web pages.


* Principles behind Compression -
1) Number of bits required to represent the information in an image can be minimized by removing the redundancy present in it.

2) There are three types of redundancies: 
	- (i) Spatial Redundancy :
	       Which is due to the correlation or dependence between neighbouring pixel values.

	- (ii) Spectral Redundancy : 
	        Which is due to the correlation between different color planes or spectral bands.

	- (iii) Temporal Redundancy : 
	         Which is present because of correlation between different frames in images.

3) Image compression aims to reduce the number of bits required to represent an image by removing the spatial and spectral redundancies as much as possible. 


* Image Compression using DCT (Discrete Cosine Transform)
1) JPEG image compression standard use DCT technique. JPEG is primarily a lossy method of compression.

2) The discrete cosine transform is a fast transform.

3) It is a widely used and robust method for image compression.

4) It has excellent compaction for highly correlated data.

5) DCT gives good compromise between information packing ability and computational complexity.


* Block Diagram 

![image](https://user-images.githubusercontent.com/76968308/118371376-fb0e3b80-b5c9-11eb-8c9f-c869812b2ee7.png)

1. Transform :
- It transforms the input data into a format to reduce interpixel redundancies in the input image.

- Transform coding techniques use a reversible, linear mathematical transform to map the pixel values onto a set of coefficients, which are then quantized and encoded.

- For compression purpose, the higher the capability of compressing information in fewer coefficients, the better the transform. For that reason, the Discrete Cosine Transform (DCT) have become the most widely used transform coding technique. 

- The forward 2D  DCT transformation is given by the following equation :

	C(h,w) = D(h) D(w) ∑_(𝑥=0)^(𝑁−1)▒∑_(𝑦=0)^(𝑁−1)▒"f(x,y) cos[(2x+1)hπ/2N] cos[(2y+1)wπ/2N]" 

	Where, h,w = 0, 1, 2, 3, ……………, N-1. 

- Transform coding algorithms usually start by partitioning the original image into subimages (blocks) of small size (usually 8 × 8).

- For each block the transform coefficients are calculated, effectively converting the original 8 × 8 array of pixel values into an array of coefficients.

- The resulting coefficients are then quantized and the output of the quantizer is used by entropy encoding techniques to produce the output bitstream representing the encoded image. 


2. Quantizer :
- It reduces the accuracy of the transformer’s output in accordance with some pre-established fidelity criterion.

- Reduces the psychovisual redundancies of the input image. The quantization stage is at the core of any lossy image encoding algorithm.

- Quantization at the encoder side, means partitioning of the input data range into a smaller set of values.

- There are two main types of quantizers :
	1. Scalar Quantizers :
	    - A scalar quantizer partitions the domain of input values into a smaller number of intervals.
	    - If the output intervals are equally spaced, which is the simplest way to do it, the process is called
	      uniform scalar quantization.

	2. Vector Quantizers : 
	    - For reasons usually related to minimization of total distortion, it is called non uniform scalar
	      quantization.
	    - Vector quantization techniques extend the basic principles of scalar quantization to multiple
	      dimensions. 


3. Entropy Encoder :
- It creates a fixed or variable-length code to represent the quantizer’s output and maps the output in accordance with the code.

- In most cases, a variable-length code is used.

- An entropy encoder compresses the compressed values obtained by the quantizer to provide more efficient compression.

- Most important types of entropy encoders used in lossy image compression techniques are arithmetic encoder, huffman encoder and run-length encoder. 


* JPEG Process -
- Original image is divided into blocks of 8 x 8.

- Pixel values of a black and white image range from 0-255 but DCT is designed to work on pixel values ranging from -128 to 127. Therefore each block is modified to work in the range. 

- DCT equation is used to calculate DCT matrix.

- DCT is applied to each block by multiplying the modified block with DCT matrix on the left and transpose of DCT matrix on its right. 

- Each block is then compressed through quantization. 

- Quantized matrix is then entropy encoded. 


* Quantization -

- Quantization is achieved by compressing a range of values to a single quantum value. 

- When the number of discrete symbols in a given stream is reduced, the stream becomes more compressible. 

- A quantization matrix is used in combination with a DCT coefficient matrix to carry out transformation. 

- Quantization is the step where most of the compression takes place. DCT really does not compress the image because it is almost lossless. 

- Quality levels ranging from 1 to 100 can be selected, where 1 gives the poorest image quality and highest compression, while 100 gives the best quality and lowest compression. 

- Matrix with quality level 50 is considered as standard matrix.


Entropy Encoding -
After quantization, most of the high frequency coefficients are zeros. To exploit the number of zeros, a zig-zag scan of the matrix is used yielding to long string of zeros. 

Once a block has been converted to a spectrum and quantized, the JPEG compression algorithm then takes the result and converts it into a one dimensional linear array, or vector of 64 values, performing a zig-zag scan by selecting the elements in the numerical order indicated by the numbers in the grid below : 
		0 		1		 2		 3	 	4	 	5	 	6		 7 
     ____________________________________________________________________________________________________________________________________
0: 		0 		1 		 5		 6		14		15		27		 28 

1:		2		4	 	 7 		13	 	 16		 26		 29		 42 

2: 		3		8	 	12 		17 		 25	 	 30		 41		 43 

3: 		9	       11	 	18 		24 		  31		 40		 44		 53 

4: 		10	       19	 	23	 	32 		  39 		 45		 52		 54

5: 		20		22 		33 		38	 	  46	 	 51 		 55		 60



** Image Reconstruction **

- Compressed image is reconstructed through reverse process. 

- Inverse DCT (IDCT) is used for reconstruction.

![image](https://user-images.githubusercontent.com/76968308/118371714-83d9a700-b5cb-11eb-85b2-80c686b0bb96.png)


1. Entropy Decoding :
- The reverse process of encoding is implemented on the receiver side and the compressed image data in the form of binary stream is decoded using Huffman dictionary and the binary stream is converted back in the symbols.


2. Dequantization :
- In the dequantization process the quantized coefficients are dequantized and inverse DCT process is applied on the dequantized coefficients which results in the decompressed image.


3. IDCT :
- The IDCT transformation is given by the following equation :

	 "f(x,y) "= ∑_(𝑢=0)^(𝑁−1)▒∑_(𝑣=0)^(𝑁−1)▒"D(u)D(v)D(u,v) cos[(2x+1)hπ/2N] cos[(2y+1)wπ/2N]" 

	Where, 
D(u) = (1/N)^1/2 for u = 0 
D(u) = (2/N)^1/2 for u = 1, 2, 3, ……., (N-1). 


*Original Images, Compressed Images and Reconstructed Images can be found in Images Folder.*
