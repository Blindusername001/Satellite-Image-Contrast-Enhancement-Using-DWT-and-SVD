# Satellite-Image-Contrast-Enhancement-Using-DWT-and-SVD
My undergrad project which is an implementation of of an IEEE paper

As part of my Engineering course, my team recreated an IEEE research paper which describes a hybrid approach to improve the contrast of image data while controlling increasing the noise data in  satellite images
 The approach uses the following techniques
1. General Histogram Equation
2. Discrete Wavelet Transform
3. Singular Value Equation


<img src="/Images%20for%20readme%20file/EmbeddedImage.png" width="650" height="400"/>



## STEP 1

<img src="/Images%20for%20readme%20file/EmbeddedImage%20(1).png" width="500" height="300"/>

A copy of an image(A) is histogram equalized. Let it be denoted as H. 
Histogram equalization spreads closely distributed contrast intensities to a more normal/ spread out    distribution.
This cannot be used as a standalone improvement for the image since this might increase the intensity of the noise data too.

## STEP 2

<img src="/Images%20for%20readme%20file/EmbeddedImage%20(2).png" width="500" height="300"/>

The histogram equalized copy of image (A) and another unprocessed copy of the image (B) are both subject to a 2-step Discrete Wavelet Transform.
The Discrete Wavelet Transform divides the image into 4 sub-brands according to frequency - LL, LH, HL, HH. 
Of the 4 bands, LL is of interest to us because it represents illumination information whereas HH represents edges.


## STEP 3
Singular Value Decomposition states that an image matrix can be represented as 

X  =  U S Vt

where U and V are orthogonal square matrices and S is a singular diagonal matrix. In image processing using SVD, the matrix S contains intensity information which is of interest to us.
We perform SVD on LL(A) and LL(B) and get the Singular matrix for both - say, S(A) & S(B). 

LL(A) = U(A) * S(A) * Vt(A)

LL(B) = U(B) * S(B) * Vt(B)

We get a correction value using both as z = S(A)/ S(B) and calculate a new image matrix using this as follows,

LL(Z) = U(B) * Z*S(B) * Vt(B)

## STEP 4
Use inverse DWT to form the updated image using,

LL(Z), LH(B), HL(B), HH(B)

This is the output image which will contain the processed LL component with improved contrast.

## References
1. H. Demirel, C. Ozcinar and G. Anbarjafari, "Satellite Image Contrast Enhancement Using Discrete Wavelet Transform and Singular Value Decomposition," in IEEE Geoscience and Remote Sensing Letters, vol. 7, no. 2, pp. 333-337, April 2010, doi: 10.1109/LGRS.2009.2034873.
2. H. Ibrahim and N. S. Pik Kong, "Brightness Preserving Dynamic Histogram Equalization for Image Contrast Enhancement," in IEEE Transactions on Consumer Electronics, vol. 53, no. 4, pp. 1752-1758, Nov. 2007, doi: 10.1109/TCE.2007.4429280.
3. H. Demirel, G. Anbarjafari and M. N. S. Jahromi, "Image equalization based on singular value decomposition," 2008 23rd International Symposium on Computer and Information Sciences, Istanbul, 2008, pp. 1-5, doi: 10.1109/ISCIS.2008.4717878.
4.  C. Gonzalez and R. E. Woods, Digital Image Processing. Englewood Cliffs, NJ: Prentice-Hall, 2007.
5. Tian, T. Tan, Y. Wang, and Y. Fang, “Do singular values contain adequate information for face recognition?” Pattern Recognit., vol. 36,no. 3, pp. 649–655, Mar. 2003.

