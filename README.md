# Dreambooth on Stable Diffusion

This is an implementtaion of Google's [Dreambooth](https://arxiv.org/abs/2208.12242) with [Stable Diffusion](https://github.com/CompVis/stable-diffusion). The original Dreambooth is based on [Imagen](https://imagen.research.google/) text-to-image model. However, neither the model nor the pre-trained weights of Imagen is available. To enable people to fine-tune a text-to-image model with a few examples, I implemented the idea of Dreambooth on Stable diffusion.

This code repository is based on that of [Textual Inversion](https://github.com/rinongal/textual_inversion). Note that Textual Inversion only optimizes word ebedding, while dreambooth fine-tunes the whole diffusion model.

The implementation makes minimum changes over the official codebase of Textual Inversion. In fact, due to lazyness, some components in Textual Inversion, such as the embedding manager, are not deleted, although they will never be used here.

## Usage

### Preparation
To fine-tune a stable diffusion model, you need to obtain the pre-trained stable diffusion models following their [instructions](https://github.com/CompVis/stable-diffusion#stable-diffusion-v1). Weights can be downloads on [HuggingFace](https://huggingface.co/CompVis). You can decide which version of checkpoint to use, but I use ```sd-v1-4-full-ema.ckpt```.

We also need to create a set of images for regularization, as the fine-tuning algorithm of Dreambooth requires that. Details of the algorithm can be found in the paper. The text prompt can be ```a class```, where ```class``` is a word that describes the class of your object, such as ```dog```. I generate 8 images for regularization. Save the generated images (separately, one image per ```.png``` file) at ```/root/to/regularization/images```.

### Training

### Generation
