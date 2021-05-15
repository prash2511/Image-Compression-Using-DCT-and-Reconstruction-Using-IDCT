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


*Block Diagram 
![image](https://user-images.githubusercontent.com/76968308/118371396-1e38eb00-b5ca-11eb-8cd9-f11db125ed09.png)

![image](https://user-images.githubusercontent.com/76968308/118371376-fb0e3b80-b5c9-11eb-8c9f-c869812b2ee7.png)
