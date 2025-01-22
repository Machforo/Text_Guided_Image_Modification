# Text-Guided Image Modification

This repository implements a novel approach to text-guided image editing, allowing complex, non-rigid transformations of real images using advanced AI diffusion models. The project preserves the original image's characteristics, enabling edits like changing posture, composition, or adding/removing objects based on text descriptions.

## Project Overview

### Objectives
- **Main Goal:** Develop a versatile and efficient method for editing real images using natural language descriptions.
- Perform complex, non-rigid edits on high-resolution real images while preserving object identity and background.
- Overcome limitations of existing methods by eliminating the need for masks or multiple input images.
- Leverage advanced diffusion models to ensure realism in output.

### Key Features
1. **Text Embedding Optimization:** Align target text embeddings with input images to extract meaningful insights using the CLIP model.
2. **Model Fine-Tuning:** Train the diffusion model with reconstruction loss to retain input image details during edits.
3. **Interpolation and Generation:** Generate the edited image by interpolating between optimized and target embeddings.

### Dataset
- **Dataset Name:** TEdBench
- Structure:
  - `Input_list.json`: Contains original image names and corresponding target text descriptions.
  - `originals/`: Directory with original images.

## Repository Structure
```
Text-Guided-Image-Modification/
├── GenAI.pptx.pdf               # Explanation report (PDF version)
├── README.md                    # Project README file
├── gen-ai-project (1).ipynb     # Notebook for text embedding optimization and fine-tuning
├── genai_Image_Reconstruction.ipynb # Notebook for image reconstruction and evaluation
```

## Links
- **Explanation Report:** [View Report](https://drive.google.com/file/d/1_hupEobeYkeqJnYtQr4l7Gda6m1w7ikD/view?usp=sharing)
- **Dataset:** [Download Dataset](https://drive.google.com/file/d/1wA8UYgiOCcOLFFNTxlYSAULGL6wkm_XW/view?usp=sharing)

## Methodology
1. **Text Embedding Optimization:**
   - Use CLIP (openai/clip-vit-large-patch14) to generate target text embeddings (`e_tgt`) and align them with input image embeddings (`e_opt`).
   - Average Cosine Similarity: **76.45%**.

2. **Model Fine-Tuning:**
   - Fine-tune the diffusion model with reconstruction loss (MSE: **5.81%**) to retain input image details during edits.

3. **Interpolation and Generation:**
   - Apply linear interpolation between `e_opt` and `e_tgt` to generate the edited image using the fine-tuned model.

## Results
- Evaluation Metrics:
  - **CLIP Score**: Measures alignment between generated image and target text (1: Perfect, -1: Opposite).
  - **SSIM Score**: Evaluates similarity between original and generated images.

Examples:
- Target: *"A photo of two bananas"*  
  - CLIP Score: **0.4308**  
  - SSIM Score: **0.3127**

- Target: *"A closed book"*  
  - CLIP Score: **0.3537**  
  - SSIM Score: **0.2621**

## Future Work
- Enhance fine-grained control for subtle edits.
- Improve alignment metrics for better semantic transformations.
- Extend the framework to handle video editing.

