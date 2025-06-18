![[15 More Neural Networks.pdf]]

With too many parameters, the vanishing gradient problem happens

<mark style="background: #ADCCFFA6;">Convolution</mark> is a form of digitally filtering one signal based on another. You can use it to model how a signal responds to certain conditions
	In image processing, you apply different filter windows, called <mark style="background: #ADCCFFA6;">kernals</mark>, to an image to get different responses
	They can sharpen, blur, edge detect, and more

A simple way to do this is to define a kernal that yields a response, say the shape of an eye, and if you multiply the input by this window, you get a version that is activated where an eye is
![[Pasted image 20250408131324.png]]

You can combine backwards propagation with kernals by turning the kernals into model parameters. Combined with stride length and pooling layers, it can rapidly reduce input image size
Guess intelligently based on kernal parameters
![[Pasted image 20250408131857.png]]
This is <mark style="background: #ADCCFFA6;">Convolution Neural Networks</mark>. Instead of many large densely-connected layers, utilize the convolution operation to help capture important image information, while rapidly reducing data complexity

![[Pasted image 20250408132007.png]]
Optimizers including momentum, static learning rate, adaptive gradient descent (AdaGrad)

The Adam gradient descent algorithm is the best one today. State of the art.

<mark style="background: #ADCCFFA6;">Embeddings</mark> are latent spaces that allow us to create optimal, minimal, quantifiable, learned representations (or features) of our data simply by example. The hidden layer basically

An <mark style="background: #ADCCFFA6;">encoder-decoder</mark> splits the network in half. The front half (encoder) takes data and stores it as the latent representation. The second half (decoder) takes the latent representation and generates the initial data again
![[Pasted image 20250408132756.png]]
Neural net where we don't finish all the interface. The decode layer finishes the inference (lossy compression)
Networks specifically for this purpose may be called <mark style="background: #ADCCFFA6;">autoencoders</mark>
