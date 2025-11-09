<div align="center">

# Text to Image Generator

# Prompt to Pixels

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.0+-green.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Maintenance](https://img.shields.io/badge/Maintained-Yes-brightgreen.svg)

*A powerful yet beginner-friendly web application that transforms <br> natural language prompts into stunning images using AI*

</div>

---

## 🌟 Overview

This project demonstrates how to integrate Stable Diffusion AI models into a Python web application using Flask and Hugging Face Diffusers. Built with simplicity in mind, it provides an intuitive interface for generating high-quality images from text descriptions, making AI-powered image generation accessible to everyone.

## ✨ Features

### Core Functionality
- ✅ **Text-to-Image Generation** - Transform natural language prompts into images
- ✅ **High-Quality Output** - Powered by Stable Diffusion v1.5
- ✅ **Image Download** - Save generated images locally
- ✅ **Responsive Design** - Works seamlessly on desktop and mobile
- ✅ **Real-time Preview** - Instant image display upon generation

### Technical Features
- 🔄 **Flexible Hardware Support** - CPU and GPU compatibility
- 📦 **Local Storage** - Generated images saved to filesystem
- 🎯 **RESTful API** - Clean API endpoints for integration
- ⚡ **Optimized Pipeline** - Efficient model loading and inference
- 🛡️ **Error Handling** - Robust error management and logging

---

## 🔧 Tech Stack

<div align="center">

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Frontend** | HTML5, CSS3, JavaScript | User interface and interactions |
| **Backend** | Python 3.8+, Flask | Web server and API endpoints |
| **AI Model** | Stable Diffusion v1.5 | Text-to-image generation |
| **ML Framework** | PyTorch, Diffusers | Model inference |
| **Storage** | Local Filesystem | Generated image storage |

</div>

### Dependencies

```
Flask >= 2.0.0
torch >= 2.0.0
diffusers >= 0.21.0
transformers >= 4.30.0
accelerate >= 0.20.0
pillow >= 9.0.0
```

---

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Python 3.8 or higher** - [Download Python](https://www.python.org/downloads/)
- **pip** - Python package installer (comes with Python)
- **Git** - [Download Git](https://git-scm.com/downloads)
- **(Optional) CUDA** - For GPU acceleration

### System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| RAM | 8GB | 16GB+ |
| Storage | 10GB free | 20GB+ free |
| GPU | None (CPU works) | NVIDIA GPU with 6GB+ VRAM |

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/ARUNAGIRINATHAN-K/text-to-image-generator.git
cd text-to-image-generator
```

### 2. Create Virtual Environment (Recommended)

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install flask torch diffusers transformers accelerate pillow
```

### 4. Create Required Directories

```bash
mkdir generated_images
mkdir static/css static/js
```

---

## 💡 Usage

### Running the Application

1. **Start the Flask server:**

```bash
python app.py
```

2. **Open your browser and navigate to:**

```
http://localhost:5000
```

3. **Generate images:**
   - Enter a descriptive text prompt (e.g., "a beautiful sunset over mountains")
   - Click "Generate Image"
   - Wait for processing (may take 30-60 seconds on CPU)
   - View and download your generated image

### Example Prompts

```
✨ "a serene lake surrounded by autumn trees, digital art"
🌆 "futuristic cityscape at night, cyberpunk style"
🐱 "cute cat wearing a wizard hat, watercolor painting"
🏔️ "majestic mountain peak with clouds, photography"
```

---

## 📁 Project Structure

```
text-to-image-generator/
├── app.py                      # Main Flask application
├── requirements.txt            # Python dependencies
├── README.md                   # Project documentation
├── .gitignore                  # Git ignore rules
├── generated_images/           # Output directory for images
├── static/
│   ├── css/
│   │   └── style.css          # Custom styles
│   └── js/
│       └── script.js          # Frontend JavaScript
├── templates/
│   └── index.html             # Main HTML template
└── models/                    # Model cache directory (auto-created)
```

---

## 🔌 API Reference

### Generate Image

**Endpoint:** `POST /generate`

**Request Body:**
```json
{
  "prompt": "your text description here"
}
```

**Response:**
```json
{
  "success": true,
  "image_url": "/generated_images/image_1234567890.png",
  "timestamp": "2025-11-07T10:30:00"
}
```

**cURL Example:**
```bash
curl -X POST http://localhost:5000/generate \
  -H "Content-Type: application/json" \
  -d '{"prompt": "a beautiful landscape"}'
```

---

## ⚙️ Configuration

### Environment Variables

Create a `.env` file in the root directory:

```env
FLASK_APP=app.py
FLASK_ENV=development
FLASK_DEBUG=1
MODEL_NAME=runwayml/stable-diffusion-v1-5
IMAGE_WIDTH=512
IMAGE_HEIGHT=512
INFERENCE_STEPS=50
```

### Customizing Generation Parameters

Edit `app.py` to adjust:

```python
# Image dimensions
image = pipe(
    prompt,
    height=512,  # Adjust height
    width=512,   # Adjust width
    num_inference_steps=50,  # Quality vs speed tradeoff
    guidance_scale=7.5  # Prompt adherence
).images[0]
```

---

## 🤖 Model Information

### Stable Diffusion v1.5

- **Model ID:** `runwayml/stable-diffusion-v1-5`
- **Type:** Text-to-Image Diffusion Model
- **License:** [CreativeML Open RAIL-M](https://huggingface.co/spaces/CompVis/stable-diffusion-license)
- **Size:** ~4GB
- **Resolution:** 512×512 (default)


---

## 🔧 Troubleshooting

### Common Issues

**Issue:** Model downloading is slow
```
Solution: First run downloads ~4GB model. Be patient or use faster internet.
```

**Issue:** Out of memory error
```
Solution: Reduce image size or use CPU instead of GPU
pipe.to("cpu")
```

**Issue:** Port 5000 already in use
```
Solution: Change port in app.py:
app.run(port=5001)
```

**Issue:** Generated images look poor quality
```
Solution: Increase inference steps in configuration (50-100 recommended)
```

## 📊 Project Stats

![GitHub stars](https://img.shields.io/github/stars/ARUNAGIRINATHAN-K/text-to-image-generator?style=social)
![GitHub forks](https://img.shields.io/github/forks/ARUNAGIRINATHAN-K/text-to-image-generator?style=social)
![GitHub issues](https://img.shields.io/github/issues/ARUNAGIRINATHAN-K/text-to-image-generator)
![GitHub pull requests](https://img.shields.io/github/issues-pr/ARUNAGIRINATHAN-K/text-to-image-generator)

---

## 🗺️ Roadmap

- [ ] Add multiple model support
- [ ] Implement image-to-image generation
- [ ] Add batch generation feature
- [ ] Create Docker container
- [ ] Add prompt suggestions
- [ ] Implement user authentication
- [ ] Add generation history
- [ ] Create mobile app

---

<div align="center">

**Made by [Arunagirinathan K](https://github.com/ARUNAGIRINATHAN-K)**

⭐ Star this repo if you find it helpful!

[Report Bug](https://github.com/ARUNAGIRINATHAN-K/text-to-image-generator/issues) • [Request Feature](https://github.com/ARUNAGIRINATHAN-K/text-to-image-generator/issues)

</div>
