# SRGAN Video Super-Resolution
Note: I implemented this in my Bachelor's of Engineering in Artificial Intelligence & Machine Learning

A Python/TensorFlow implementation that applies **Super-Resolution Generative Adversarial Networks (SRGAN)** to video files, upscaling each frame and reconstructing a high-resolution output video.

---

## Overview

This project takes a low-resolution video, extracts its individual frames, runs each frame through a pretrained SRGAN generator model to produce super-resolved versions, and then stitches the enhanced frames back together into a new video. The result is a visually sharper, higher-resolution video compared to the original.

---

## How It Works

1. **Frame Extraction** — The input video is read using OpenCV and each frame is saved as a JPEG image to a local `data/` directory.
2. **Super-Resolution** — Each extracted frame is passed through the pretrained SRGAN generator (`gan_generator.h5`), which upscales the image by 4×.
3. **Frame Saving** — The super-resolved frames (in NumPy array format) are converted back to images and saved to an output directory.
4. **Video Reconstruction** — The enhanced frames are compiled back into an `.mp4` video using OpenCV's `VideoWriter`.

---

## Requirements

- Python 3.x
- TensorFlow / Keras
- OpenCV (`opencv-python`)
- NumPy

Install dependencies:

```bash
pip install tensorflow opencv-python numpy
```

---

## Setup

1. Clone the pretrained SRGAN model repository:

```bash
git clone https://github.com/krasserm/super-resolution
cd super-resolution
```

2. Download and extract the pretrained SRGAN weights:

```bash
tar xvfz weights-srgan.tar.gz
```

3. Place your input video in the working directory (e.g., `Cute_Panda_eating_grass.mp4`).

---

## Usage

Run the notebook cells in order within **Google Colab** or a local Jupyter environment:

1. Install dependencies and clone the model repo.
2. Extract frames from your input video.
3. Apply the SRGAN model to each frame.
4. Save the super-resolved frames as images.
5. Compile the frames into an output video (`output_videos/panda2.mp4`).

To use a different video, update the `cv2.VideoCapture(...)` path in the frame extraction cell.

You can also adjust the output **FPS** in the video reconstruction step:

```python
fps = 10  # set this to match the original video or your preference
```

---

## Output

- **Super-resolved frames** are saved to: `super-resolution/output_images/`
- **Final video** is saved to: `super-resolution/output_videos/panda2.mp4`

---

## Notes

- This notebook is designed to run on **Google Colab** (paths reference `/content/`). Adjust directory paths if running locally.
- Processing time scales with the number of frames. A timing report is printed after inference.
- The SRGAN model upscales images by a factor of **4×**, so output frames will be significantly larger than the input.

---

## References

- Original SRGAN paper: [Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network](https://arxiv.org/abs/1609.04802)
- Pretrained model: [krasserm/super-resolution](https://github.com/krasserm/super-resolution)
