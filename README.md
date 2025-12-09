# 🧩 Sudoku Solver AI Web App

<div align="center">

**An intelligent full-stack web application that detects and solves Sudoku puzzles from images using AI-powered digit recognition and optimized solving algorithms.**

[![GitHub](https://img.shields.io/badge/GitHub-Repository-blue?style=flat-square&logo=github)](https://github.com/Subhmakesachange/sudoku)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

**Made with ❤️ by [Subhajeet Baskey](https://github.com/Subhmakesachange)**

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [How It Works](#-how-it-works)
- [Installation & Setup](#-installation--setup)
- [Usage](#-usage)
- [API Documentation](#-api-documentation)
- [Performance](#-performance)
- [Future Enhancements](#-future-enhancements)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Overview

This project combines the power of **Computer Vision**, **Machine Learning**, and **Optimized Algorithms** to create an end-to-end Sudoku solving experience. Simply upload an image of a Sudoku puzzle, and the application will:

1. **Detect** the Sudoku grid using OpenCV
2. **Recognize** digits using a trained CNN model
3. **Allow** manual corrections for accuracy
4. **Solve** the puzzle using blazing-fast C-based algorithms
5. **Display** the solution in an intuitive interface

---

## ✨ Features

### 🖼️ Image Processing
- **Automatic Grid Detection**: Uses OpenCV to detect and isolate Sudoku grids from uploaded images
- **Preprocessing Pipeline**: Image enhancement, perspective correction, and noise reduction
- **Cell Extraction**: Intelligent segmentation of individual cells

### 🤖 Machine Learning
- **CNN-Based Recognition**: Deep learning model trained on digit recognition
- **High Accuracy**: Robust digit prediction from various image qualities
- **Multiple Models**: Support for different model architectures (MNIST, custom trained)

### ⚡ Performance
- **Ultra-Fast Solving**: C-based solver completes puzzles in under 10ms
- **Multi-Language Support**: Solvers available in C, C++, Go, and Python
- **Optimized Algorithms**: Backtracking with constraint propagation

### 🎨 User Experience
- **Interactive Grid**: Edit detected digits before solving
- **Real-time Validation**: Instant feedback on puzzle validity
- **Modern UI**: Built with React, TypeScript, and Tailwind CSS
- **Responsive Design**: Works seamlessly on desktop and mobile devices

### 🔧 Technical Features
- **Dual Backend Support**: Both Flask and FastAPI implementations
- **RESTful API**: Clean, well-documented endpoints
- **Error Handling**: Comprehensive error handling and validation
- **CORS Support**: Configured for cross-origin requests

---

## 🚀 Tech Stack

### Frontend
- **React 18+** - UI framework
- **TypeScript** - Type safety
- **Vite** - Build tool and dev server
- **Tailwind CSS** - Styling
- **TanStack Query** - Data fetching
- **Axios** - HTTP client
- **shadcn/ui** - UI component library

### Backend
- **Flask** - Python web framework (primary backend)
- **FastAPI** - Modern Python API framework (alternative backend)
- **Python 3.8+** - Backend language

### Machine Learning
- **TensorFlow/Keras** - Deep learning framework
- **OpenCV** - Computer vision library
- **NumPy** - Numerical computing
- **Pillow** - Image processing

### Algorithms
- **C** - Fastest solver implementation (< 10ms)
- **C++** - High-performance alternative
- **Go** - Concurrent solver implementation
- **Python** - Reference implementation (< 200ms)

---

## 🏗️ Architecture

```
┌─────────────┐
│   Frontend  │  React + TypeScript + Vite
│   (React)   │
└──────┬──────┘
       │ HTTP/REST
       │
┌──────▼──────┐
│   Backend   │  Flask/FastAPI
│  (Python)   │
└──────┬──────┘
       │
   ┌───┴───┐
   │       │
┌──▼──┐ ┌──▼────┐
│ ML  │ │ Solver│
│Model│ │  (C)  │
└─────┘ └───────┘
```

### Workflow
1. **Image Upload** → Frontend receives image file
2. **Grid Detection** → Backend processes image with OpenCV
3. **Digit Recognition** → CNN model predicts digits for each cell
4. **User Verification** → Frontend allows manual corrections
5. **Puzzle Solving** → C-based solver generates solution
6. **Result Display** → Frontend renders solved puzzle

---

## 📂 Project Structure

```
sudoku/
├── algo/                          # Solver implementations
│   ├── sudoku_solver.c           # C implementation (fastest)
│   ├── sudoku_solver.cpp         # C++ implementation
│   ├── sudoku_solver.go          # Go implementation
│   ├── sudoku_solver_generalize.py
│   └── sudoku_solver_opt_gen.py
│
├── backend_flask/                 # Flask backend
│   ├── app.py                    # Main Flask application
│   ├── model_wrapper.py          # ML model wrapper
│   ├── sudoku_solver_optimized.py
│   ├── requirements.txt
│   └── model/                    # Trained models
│       ├── full_model.h5
│       ├── sudoku_model.h5
│       └── mnist_weights.h5
│
├── backend_fastAPI/               # FastAPI backend
│   ├── main.py                   # FastAPI application
│   ├── requirements.txt
│   ├── model/
│   │   ├── model.py
│   │   └── trained_pipeline_model.h5
│   ├── solver_algo/
│   │   └── sudoku_solver_optimized.py
│   └── llm/
│       └── llm_predict.py
│
├── frontend/                      # React frontend
│   ├── src/
│   │   ├── components/           # React components
│   │   ├── pages/                # Page components
│   │   ├── api/                  # API client
│   │   ├── hooks/                # Custom hooks
│   │   └── lib/                  # Utilities
│   ├── public/
│   ├── package.json
│   └── vite.config.ts
│
├── notebook/                      # Jupyter notebooks
│   └── sudoku_model_training_gc.ipynb
│
├── images/                        # Sample test images
│   ├── 1.png
│   ├── 2.png
│   ├── 3.png
│   ├── 4.png
│   └── 5.jpg
│
├── sudoku_solver.py              # Standalone solver
├── .gitignore
└── README.md
```

---

## ⚙️ How It Works

### 1. Image Processing Pipeline
```
Upload Image → Preprocess → Detect Grid → Extract Cells → Normalize
```

### 2. Digit Recognition
```
Cell Image → CNN Model → Digit Prediction → Confidence Score
```

### 3. Solving Algorithm
```
Grid Input → Validation → Backtracking Algorithm → Solution
```

### Detailed Steps:
1. **Image Upload**: User uploads a Sudoku puzzle image
2. **Preprocessing**: Image is converted to grayscale and enhanced
3. **Grid Detection**: OpenCV detects the Sudoku grid boundaries
4. **Perspective Correction**: Grid is transformed to a square
5. **Cell Extraction**: 81 individual cells are extracted
6. **Digit Recognition**: Each cell is fed to the CNN model
7. **User Review**: Detected digits are displayed for verification
8. **Manual Correction**: User can edit any incorrect predictions
9. **Validation**: System validates the puzzle is solvable
10. **Solving**: C-based solver generates the solution
11. **Display**: Solved puzzle is shown with visual feedback

---

## 📦 Installation & Setup

### Prerequisites
- **Node.js** 18+ and npm
- **Python** 3.8+
- **GCC** (for compiling C solver)
- **Git**

### Step 1: Clone the Repository

```bash
git clone https://github.com/Subhmakesachange/sudoku.git
cd sudoku
```

### Step 2: Backend Setup (Flask)

```bash
# Navigate to backend directory
cd backend_flask

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Compile C Sudoku Solver
# On Windows (using MinGW or MSVC):
gcc -shared -o ../algo/lib_sudoku_solver.dll -fPIC ../algo/sudoku_solver.c
# On macOS/Linux:
gcc -shared -o ../algo/lib_sudoku_solver.so -fPIC ../algo/sudoku_solver.c

# Verify model exists
# Ensure backend_flask/model/full_model.h5 exists

# Start Flask server
python app.py
```

The Flask server will run on `http://localhost:5000`

### Step 3: Backend Setup (FastAPI - Alternative)

```bash
cd backend_fastAPI

# Create and activate virtual environment (same as above)
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows

# Install dependencies
pip install -r requirements.txt

# Run FastAPI server
uvicorn main:app --reload
```

The FastAPI server will run on `http://localhost:8000`

### Step 4: Frontend Setup

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Create environment file
# Create .env file with:
VITE_BACKEND_URL=http://localhost:5000
# For FastAPI backend, use:
# VITE_BACKEND_URL=http://localhost:8000

# Start development server
npm run dev
```

The frontend will run on `http://localhost:5173` (or another port if 5173 is busy)

---

## 🎮 Usage

### Basic Workflow

1. **Start Backend**: Run the Flask or FastAPI server
2. **Start Frontend**: Run the React development server
3. **Open Browser**: Navigate to `http://localhost:5173`
4. **Upload Image**: Click "Upload" and select a Sudoku puzzle image
5. **Review Predictions**: Check the detected digits
6. **Edit if Needed**: Click on any cell to correct predictions
7. **Solve**: Click the "Solve" button
8. **View Solution**: The solved puzzle will be displayed

### Sample Images

Test the application with sample images from the `images/` directory:
- `1.png`, `2.png`, `3.png`, `4.png`, `5.jpg`

---

## 🛠 API Documentation

### Flask Backend Endpoints

#### `POST /predict`
Upload an image and get predicted Sudoku grid.

**Request:**
- Method: `POST`
- Content-Type: `multipart/form-data`
- Body: Image file

**Response:**
```json
{
  "grid": [
    [0, 0, 3, 0, 2, 0, 6, 0, 0],
    [9, 0, 0, 3, 0, 5, 0, 0, 1],
    ...
  ],
  "confidence": 0.95
}
```

#### `POST /solve`
Submit a Sudoku grid and get the solution.

**Request:**
- Method: `POST`
- Content-Type: `application/json`
- Body:
```json
{
  "grid": [
    [0, 0, 3, 0, 2, 0, 6, 0, 0],
    ...
  ]
}
```

**Response:**
```json
{
  "solved": true,
  "solution": [
    [4, 3, 5, 2, 6, 9, 7, 8, 1],
    ...
  ],
  "time_taken": 0.008
}
```

#### `GET /`
Health check endpoint.

**Response:**
```
Hello World!
```

### FastAPI Backend

FastAPI provides automatic interactive documentation at:
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

---

## ⚡ Performance

### Solver Performance Comparison

| Language | Average Time | Best Case | Worst Case |
|----------|--------------|-----------|------------|
| **C** | < 10ms | < 5ms | < 15ms |
| **C++** | < 15ms | < 8ms | < 20ms |
| **Go** | < 20ms | < 10ms | < 30ms |
| **Python** | < 200ms | < 100ms | < 300ms |

### Model Performance
- **Digit Recognition Accuracy**: ~95%+
- **Grid Detection Success Rate**: ~98%+
- **Average Processing Time**: 2-5 seconds (image → grid)

---

## 🔮 Future Enhancements

### Planned Features
- [ ] **Enhanced Recognition**: Better digit recognition with data augmentation
- [ ] **Animated Visualization**: Step-by-step solving animation
- [ ] **Multiple Difficulty Levels**: Easy, Medium, Hard puzzle generation
- [ ] **Dark/Light Mode**: Theme toggle for better UX
- [ ] **Puzzle Generator**: Generate random valid Sudoku puzzles
- [ ] **Mobile App**: Native mobile application
- [ ] **Batch Processing**: Solve multiple puzzles at once
- [ ] **Export Options**: Download solved puzzle as PDF/image
- [ ] **History**: Save and view previously solved puzzles
- [ ] **Multiplayer**: Compete with friends in solving speed

### Technical Improvements
- [ ] **Model Optimization**: Quantization and pruning for faster inference
- [ ] **Caching**: Cache model predictions for similar images
- [ ] **WebSocket**: Real-time updates during solving
- [ ] **Docker**: Containerization for easy deployment
- [ ] **CI/CD**: Automated testing and deployment pipeline
- [ ] **Monitoring**: Performance monitoring and analytics

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines
- Follow existing code style
- Add comments for complex logic
- Update documentation as needed
- Write tests for new features

---

## 🙏 Acknowledgements

This project uses the following amazing open-source libraries and frameworks:

- **[TensorFlow](https://www.tensorflow.org/)** - Machine learning framework
- **[OpenCV](https://opencv.org/)** - Computer vision library
- **[Flask](https://flask.palletsprojects.com/)** - Python web framework
- **[FastAPI](https://fastapi.tiangolo.com/)** - Modern Python API framework
- **[React](https://react.dev/)** - JavaScript UI library
- **[TypeScript](https://www.typescriptlang.org/)** - Typed JavaScript
- **[Vite](https://vitejs.dev/)** - Next-generation frontend tooling
- **[Tailwind CSS](https://tailwindcss.com/)** - Utility-first CSS framework
- **[shadcn/ui](https://ui.shadcn.com/)** - Beautiful UI components

---

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

You are free to:
- ✅ Use the code commercially
- ✅ Modify the code
- ✅ Distribute the code
- ✅ Use privately

---

## 👤 Author

**Subhajeet Baskey**

- GitHub: [@Subhmakesachange](https://github.com/Subhmakesachange)
- Repository: [sudoku](https://github.com/Subhmakesachange/sudoku)

---

## ⭐ Show Your Support

If you find this project helpful, please consider giving it a ⭐ on GitHub!

---

<div align="center">

**Made with ❤️ by Subhajeet Baskey**

*Solving Sudoku puzzles, one pixel at a time* 🧩

</div>
