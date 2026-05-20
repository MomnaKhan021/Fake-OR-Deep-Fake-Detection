Universal Fake Image Detection

Towards Universal Fake Image Detectors that Generalize Across Generative Models
Paper: Ojha, U., Li, Y., & Lee, Y. J. - CVPR 2023 Paper PDF: https://openaccess.thecvf.com/content/CVPR2023/papers/Ojha_Towards_Universal_Fake_Image_Detectors_That_Generalize_Across_Generative_Models_CVPR_2023_paper.pdf arXiv: https://arxiv.org/abs/2302.10174 Project Page: https://utkarshojha.github.io/universal-fake-detection/ Official GitHub: https://github.com/WisconsinAIVision/UniversalFakeDetect

Team Members
Name	Registration No.	Role
Hafsa Saleem	MSCS25004	Repository setup, data pipeline
Amna Ghulam Nabie	MSCS25018	Model loading & CLIP feature extraction
Momna Waryam Khan	MSCS25011	Code implementation, Evaluation, Metrics, and Demo preparation
Key Idea of the Paper
Traditional fake-image detectors are trained as a deep binary classifier on REAL vs. FAKE images from one generative model (for example, ProGAN). When tested on images from a different generative family (for example, Diffusion, GLIDE, LDM), they fail badly.

The authors propose a strikingly simple alternative:

Take a frozen CLIP ViT-L/14 image encoder (never trained for fake detection)
Extract 768-dimensional features from input images
Train only a single linear layer on top, for binary classification (REAL vs FAKE)
This tiny model generalizes remarkably well across GANs, diffusion models, and other generative families, beating much heavier supervised baselines.

What is new in this version of the notebook
This notebook has been extended beyond the original demo:

Large real dataset from Kaggle - the model is now evaluated on the CIFAKE dataset (Bird & Lotfi, 2024), a 120,000-image benchmark (60,000 real CIFAR-10 images and 60,000 Stable-Diffusion-generated fakes) downloaded automatically through kagglehub. The number of evaluated images is configurable so it still runs comfortably on a Colab GPU.
The small 3-real / 3-fake sample is kept as a fast fallback when Kaggle credentials are not available.
Image demo works from upload, webcam, and clipboard - the input sources are now declared explicitly so the camera button always appears.
Video support added - a separate demo tab samples frames from an uploaded or webcam-recorded video, runs the detector on each sampled frame, and aggregates the per-frame scores into a single REAL/FAKE verdict.
How to run this notebook
File -> Upload notebook in Colab
Runtime -> Change runtime type -> T4 GPU
Run cells top to bottom
Pretrained weights and the CLIP model are downloaded automatically
For the Kaggle dataset, add your Kaggle API token when prompted (instructions are in Step 6)
