# Fashion Item Identification System with VQA
Selection test for HVAR

## Introduction
Welcome to the Visual Question Answering (VQA) project for identifying fashion items in images. This system was developed to innovate the interaction of European fashion brands with their audience, using machine learning to identify fashion items in visual media and find similar products.

## Context
This project was developed after a European fashion sector client expressed interest in innovating their interaction with the public through machine learning. Hvar Consulting was tasked with developing a solution that allows for the identification of fashion items in images or videos and to suggest similar products from the company's catalog.

## Objective
We will use the [SaffalPoosh/deepFashion-with-masks](https://huggingface.co/datasets/SaffalPoosh/deepFashion-with-masks) dataset to train the [ViLT](https://huggingface.co/docs/transformers/model_doc/vilt) and pre-trained [BLIP](https://huggingface.co/Salesforce/blip-vqa-base) models. The ViLT model is geared towards a more categorical analysis of images, while the BLIP model is for identifying items in a more contextual manner. We will fine-tune these models, teaching ViLT to identify clothing categories and BLIP to describe the items and characteristics of the images in a more contextual way.

## Requirements
Install the following libraries:
```bash
pip install datasets
pip install transformers[torch]
pip install accelerate -U
pip install gradio
pip install huggingface_hub
```
## Usage
You can clone this repository to the environment of your choice or access the following colab to execute the code: [Evaluation](https://colab.research.google.com/drive/1w9R-bZE4V3jEKxAzOhpGGd7svBRWE8vg?usp=sharing)

### Details of the Python notebook `avaliacao.ipynb`
**- Library Installation:** Installation of the necessary libraries for the project.

**- Preliminary Analysis of Pre-trained Models:** In this stage, it is possible to perform analyses and tests with the models that we will fine-tune. You can submit an image and a question through the Gradio tool and receive the models' output on the Gradio panel. Some images used for this evaluation and excluded from the models' fine-tuning are available in the `images` directory.

![Test01](/imgs_readme/test01.png)

**- Huggingface Hub Login:** It is necessary to authenticate with your token generated on [Hugging Face](https://huggingface.co/) to later push the models to a repository on the platform.

**- Training of Blip and ViLT:** In this stage, we perform the necessary treatments of images and texts, train the ViLT and BLIP models, and push each of the models to their respective repositories on Hugging Face.

**- Model Evaluation After Fine-tuning:** In this stage, we perform an evaluation of the models after fine-tuning using the Gradio tool for evaluation, tests can be performed with the same images from the `images` directory highlighted in the **Preliminary Analysis of Pre-trained Models** stage. It is also already configured to fetch the models which I, Matheus de Ornelas, trained and pushed to Hugging Face, these are the repositories of the two models: [BLIP](https://huggingface.co/Ornelas/blip_finetuned_fashion) and [ViLT](https://huggingface.co/Ornelas/vilt_finetuned_fashion).

![Test02](/imgs_readme/test02.png)

## Results
We observed that in the initial evaluation, the ViLT model did not return any categories, however, after fine-tuning, we obtained good results, albeit superficial. We believe that with some adjustments to the data and the addition of more data and model hyperparameter tuning, an improved result can be achieved. Regarding the BLIP model, we noticed that in the initial evaluation, it also did not return satisfactory results. However, after fine-tuning the model, we observed a very good result. Even with a simple model and limited data, we obtained satisfactory results, where we could identify a significant amount of fashion categories in the images with acceptable context.

## Contribution
Developed by Matheus de Ornelas Vasconcellos, this project reflects the commitment to providing innovative solutions, using cutting-edge technologies in machine learning and computer vision. I appreciate the opportunity and challenge proposed by Valerio Cardoso, collaborator at HVAR.

## License
This project is licensed under the terms of the MIT License. This allows for broad use, including commercial and modification uses, provided that proper credit is given to the original developer, Matheus de Ornelas Vasconcellos, and contributors. The MIT License is known for its permissiveness and is one of the most popular software licenses in the open source world.

For more details about the license, consult the `LICENSE` file in the GitHub repository.
