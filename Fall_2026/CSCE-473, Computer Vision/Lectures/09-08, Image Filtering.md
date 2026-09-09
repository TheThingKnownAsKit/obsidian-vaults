![[Image Filtering.pdf]]

Three ways to filter images, through the spatial domain, the frequency domain, or using image pyramids

Filtering in the <mark style="background: #ADCCFFA6;">spatial domain</mark> means using a mathematical operation with a grid of numbers to smooth, sharpen, or measure texture. Think back to Polsley's class
Filtering in the <mark style="background: #ADCCFFA6;">frequency domain</mark> is modifying the frequency of images. Denoising, sampling, and image compression
Filtering with <mark style="background: #ADCCFFA6;">templates and image pyramids</mark> is matching a template to the image to for image detection and coarse-to-fine registration
TLDR:
- Enhance images
	- Denoise, resize, increase contrast, etc
- Extract information from images
	- Texture, edges, distinctive points, etc
- Detect patterns
	- Template matching

Remember convolution matrices from Polsley's class. Input image and a kernel/filter that generates an image as the output