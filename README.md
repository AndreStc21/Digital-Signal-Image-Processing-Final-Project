# Digital-Signal-Image-Processing-Final-Project

My final project for a university course in Digital Signal & Image Processing

## 1. What the project is about

The project is about the implementation of 2D Haar Wavelet Transform (HWT) for image compression. It's not the best way to perform compression, since usually it's used mainly for denoising, but they're a good starting point to understand how 2D wavelets work and how they can be used to compress data.

HWT basically relies on computing a sparse or nearly sparse matrix from the image matrix, in that these kind of matrices, having a great amount of entries to zero, can be stored in a more efficient way, leading to smaller file sizes. 

I decided to adopt the block-based image compression in order not to have to deal with too big transformation matrices, since the size of the matrix is proportional to the size of the image. So, the image is divided in blocks of 8x8 pixels and the HWT is applied to each block.

First the grayscale case is analyzed, then the color case is considered.

I explored a bit lossless compression but mainly lossy compression since the former it's kind of trivial. In lossy compression a threshold is applied to the transformed matrix, in order to set to zero all the entries below it. Subsequently, I analyzed the compression ratio (CR) and the peak signal-to-noise ratio (PSNR) for different values of the threshold. Then, I explored a bit the concept of Progressive Image Transmission (PIT), where the image is compressed in a way that allows to obtain a low quality version of the image, and then, by adding more information, a better quality version of the image can be obtained. This is useful in case of transmission of images over a network, where the image can be sent in a low quality version first, and then, if the user wants, the image can be sent in a better quality version.

Finally, I analyzed the RGB case in which everything is the same except that the transformation has to be applied to the three channels of the image.

## 2. Obtained results

The HWT effectively compresses images in a reasonable way, but only when we adopt lossy compression because the lossless one doesn't perform such a good job. The problem with lossy compression is that we have a trade-off between CR and PSNR, so we have to find a good compromise between the two: we want to compress our image as much as possible, but we also want to keep the quality of the image as high as possible. This is of course doable, but obviously if we want to consistensly compress the image, we have to accept a certain loss of quality.

Overall, 2D HWT is a reasonable technique in order to compress data since they’re easy to understand, to implement and they yield fair results. The main issue is that lossless compression isn't that useful, since it doesn't compress the image that much, and lossy compression is effective to the detriment of quality.

There are better alternatives: Daublechies, Coiflets and Biorthogonal wavelets are a good match for instance, but they're obviously more complex to implement and to understand. If you don't want to stick with wavelets instead, your best bet should be the discrete cosine transform.
