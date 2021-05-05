# Super-Resolution-GAN
The SRGAN, introduced in 2016, addressed the issue of reconstructing high resolution (HR) images from low resolution (LR) images such that fine texture detail in the reconstructed super resolution (SR) images was not lost. Here the authors used a perceptual loss instead of a pixel-wise Mean Squared Error (MSE) loss. MSE loss approaches give a high Peak Signal-to-Noise (PSNR) value, but they also tend to produce overly-smooth images with insufficient high-frequency details. The perceptual loss by contrast has a content loss component that computes pixel-wise differences in feature space (not pixel space) and this results in an SR image that is closer to the subjective evaluation of human observers.

The SRGAN model uses a deep neural network (built with residual blocks) and optimized using perceptual loss in a GAN framework. A VGG-19 network is used for feature extraction; this allows us to compute the feature distance between the original and generated images sent through the feature extractor.

In this exercise we use an SRGAN design which is faithful to the original SRGAN [2]. This architecture used a pre-trained VGG-19 feature extractor and gave photorealistic results on large (4x) upsampled low resolution images. It has been applied to the DIV2K, CelebA and other natural image datasets and here we want to see how it performs on OCT data. This network will serve as a baseline for further experiments with upscaling, choice of feature extractor etcetera.

<hr>
<b>Working of Model</b>
<ol type="1">
  <li>We downsample HR OCT images by 4x to synthetically create LR training data. This gives us pairs of HR and LR images for the training data set.</li>
  <li>The Generator upsamples LR images by 4x and will be trained to generate SR images.</li>
  <li>The discriminator will be trained to distinguish between HR/SR images; the GAN loss is backpropagated to the discriminator and the generator.</li>

<hr>
<b>Architecture</b>
<img src="https://paperswithcode.com/media/methods/Screen_Shot_2020-07-19_at_11.13.45_AM_zsF2pa7.png"/>

<hr>
<b>Evaluation</b><br>
The visual quality of generated images will be observed. In addition standard quantitative metrics, Peak Signal-to-Noise Ratio and Structural Similarity Index (PSNR, SSIM), will be used to assess the results

<figure class="video_container">
<iframe src="https://www.kaggle.com/embed/shir0mani/enhancing-oct-image-resolution-with-srgan?cellId=14&cellIds=14&kernelSessionId=44502913" height="300" style="margin: 0 auto; width: 100%; max-width: 950px;" frameborder="0" scrolling="auto" title="Enhancing OCT image resolution with SRGAN "></iframe>
</figure>
<figure>
<iframe src="https://www.kaggle.com/embed/shir0mani/enhancing-oct-image-resolution-with-srgan?cellId=14&cellIds=17&kernelSessionId=44502913" height="300" style="margin: 0 auto; width: 100%; max-width: 950px;" frameborder="0" scrolling="auto" title="Enhancing OCT image resolution with SRGAN "></iframe>
</figure>
