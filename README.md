# Installing Detectron2 on a Mac in CPU mode

  At the risk of saying, “Yeah, it’s in the docs,” this is what I did. I think the crucial thing is installed things in the proper order, so I would advise going step-by-step:

1. Have conda installed (brew install conda if not, I suppose)
2. Create a conda environment with conda create -n detectron2 python=3.9 conda activate detectron2
3. Install PyTorch and Torchvision via [this page] choosing “Stable” / “Mac” / “Conda” / “Python” / “CPU”: conda install pytorch torchvision torchaudio -c pytorch
4. Install OpenCV with conda install -c conda-forge opencv
5. Install Detectron2 via [this page] python -m pip install 'git+https://github.com/facebookresearch/detectron2.git' (Oddly, this didn’t appear to actually compile anything on my M1-based Mac Mini. I did not prepend ARCHFLAGS and CC and CXX as described at the Detectron2 install page. )
6. Then, you should be able to locally run, e.g., the code from [the tutorial]. But! YOU MUST add cfg.MODEL.DEVICE = 'cpu' to your configuration.

It may be possible to fine-tune Detectron2 using CPU-mode, although it will certainly be much slower than doing so in GPU mode. But for inferencing, CPU-mode seems to work fine.
