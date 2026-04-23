# Wav2Lip (CPU, Windows, Conda Setup)

This guide helps you run **Wav2Lip** locally on a Windows machine without GPU using Conda.

---

## 📦 Requirements

* Windows 10/11
* Miniconda / Anaconda
* FFmpeg (installed and added to PATH)

---

## ⚙️ Setup (Conda Only)

### 1. Clone Repository

```
git clone https://github.com/Rudrabha/Wav2Lip.git
cd Wav2Lip
```

---

### 2. Create Environment

```
conda env create -f environment.yml
conda activate wav2lip
```

👉 No need to install `requirements.txt`

---

## 📥 Model Setup

Download model file and place here:

```
Wav2Lip/checkpoints/wav2lip.pth
```

OR (for low-end systems):

```
Wav2Lip/checkpoints/Wav2Lip-SD-NOGAN.pt
```

---

## ▶️ Run Inference

### Single-line (CMD)

```
python inference.py --checkpoint_path checkpoints\wav2lip.pth --face assets\face.jpg --audio assets\test.wav --outfile output.mp4 --resize_factor 3 --nosmooth
```

---

## 🔊 Fix Audio (if missing)

Sometimes audio is not merged automatically.

Run manually:

```
ffmpeg -y -i temp\result.avi -i assets\test.wav -c:v copy -c:a aac output_final.mp4
```

---

## ⚠️ Notes

* CPU execution is slow (5–15 min for short video)
* Use short clips (≤10 sec)
* Prefer image input over video for better performance
* Lower resolution improves speed

---

## 🧠 Tips for Low-End PC (8GB RAM)

* Use `--resize_factor 3` or `4`
* Use `.jpg` instead of video
* Close other apps while running

---

## 🧪 Test Files

Use:

* `assets/test.wav` (audio)
* `assets/face.jpg` (image)

---

## ❌ Common Issues

### Missing modules

```
pip install tqdm opencv-python librosa
```

### No audio in output

* Ensure FFmpeg is installed
* Merge manually (see above)

### Model loading error (.pt vs .pth)

* `.pth` works directly
* `.pt` requires small code patch
