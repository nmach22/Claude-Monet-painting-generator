# Claude-Monet-painting-generator

[kaggle link](https://www.kaggle.com/competitions/gan-getting-started)

[Wandb report link](https://wandb.ai/nmach22-free-university-of-tbilisi-/Generate%20Monet%20paintings/reports/CycleGAN-for-Monet-style-Painting-Generation-A-Comparison-of-U-Net-and-ResNet-Architectures--VmlldzoxNTU5MTc0MA)

## Model Architectures

This project explores two different generator architectures for a CycleGAN model to translate photos into Monet-style paintings.

### 1. ResNet-based Generator

The first model uses a generator based on Residual Blocks (ResNet).

#### Generator

The generator architecture is as follows:
1.  An initial convolution layer.
2.  Two down-sampling convolution layers.
3.  A series of residual blocks (6 by default).
4.  Two up-sampling transposed convolution layers.
5.  A final convolution layer to produce the output image.

The residual blocks allow the model to learn identity functions, which helps in training deeper networks.

#### Discriminator

The discriminator is a standard convolutional network that classifies images as real or fake. It consists of a series of convolutional layers with LeakyReLU activations, progressively reducing the spatial dimensions of the input.

### 2. U-Net-based Generator

The second model uses a generator with a U-Net architecture.

#### Generator (U-Net)

The U-Net generator has an encoder-decoder structure with skip connections:
*   **Encoder:** A series of down-sampling convolutional layers capture contextual information from the input image.
*   **Bottleneck:** A middle layer that connects the encoder and decoder.
*   **Decoder:** A series of up-sampling transposed convolutional layers that reconstruct the image.
*   **Skip Connections:** These connections link the encoder layers directly to their corresponding decoder layers, allowing the decoder to access high-resolution features from the encoder. This helps in generating more detailed images.

#### Discriminator (PatchGAN)

This model uses a PatchGAN discriminator. Instead of classifying the entire image as real or fake, the PatchGAN discriminator classifies overlapping patches of the image. This encourages the generator to produce high-frequency details and improves the quality of the generated images. The output of the discriminator is a matrix of predictions, where each value corresponds to a patch of the input image.

