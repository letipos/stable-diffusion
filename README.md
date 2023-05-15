## Stable Diffusion. What's the hype ? 

Diffusion models are quite in the hype for Text-to-Image generation. We all have seen the weird videos on the Internet of Text-to-Image generation, but how does it even work ?

### Noising and Denoising : 
We'll start with the easy part. Denoising refers to process of removing noise from the image and Noising refers to the process of adding noise to an image. That sounds easy. Can there be any problem in this simple task ?

It turns out that generally, the image synthesis tasks are performed by deep geenrative models(such as GANs, VAEs, and autoregressive models) which has its downsides when trained to synthsize high quality samples on difficult, high resolution datasets. 

Maybe - we can just break down this process of noising and denoising into smaller, managable chunks ? ...  

### What is Diffusion ?

The answer to the last question is **Diffusion models**. 

The idea behind diffusion is quite simple. Firstly, we'll start with corrupting the training data iteratively by adding gaussian noise, slowly wiping out the details till it becomes pure noise, and then training a model to reverse this corruption process(which is also done iteratively) 

This process of de-corrupting the image is also quite clever and happens over several iterations. Instead of directly generating the image, (which can be quite not so accurate and have some ambiguities) we ask the denoising model(also called backward process) to try to predict the noise itself !(again, keep in mind that this is done at a particular iteration). Then , we just subtract the noise from the image.

It turns out that this is much more accurate than directly generating the image. 