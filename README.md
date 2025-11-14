# Multimodal Omics Registration

The repository is a collection of scripts used in the ScOpenLab for the registration of multiomics datasets.
The repository is still a work in progress, and scripts/docs will be updated.

Most scripts are adaptations of the registration workflow shown at:
https://spatialdata.scverse.org/en/stable/tutorials/notebooks/notebooks/examples/alignment_using_landmarks.html
The scripts automate the workflow by using SIFT(https://docs.opencv.org/4.x/da/df5/tutorial_py_sift_intro.html) to identify landmarks for the registration, instead of having the user manually selecting landmarks.

## Structure
The repository is divided by technologies being registered:
- Xenium-CODEX
- Xenium-COMET
- ...

There is also a folder with instructions and scripts for visualization with Napari:
- [Napari_UI_scripts](https://github.com/scOpenLab/MultimodalRegistration/tree/main/Napari_UI_scripts)

Please find more detailed instructions in each subfolder.

