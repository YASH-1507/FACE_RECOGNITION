# Face Recognition System

A Python-based face recognition tool that detects and identifies known faces in images using OpenCV and the `face_recognition` library.

## What it does

- Scans a `faces/` directory to build an encoded database of known faces
- Takes an input image and locates all faces in it
- Compares detected faces against the known database using facial distance metrics
- Draws bounding boxes and labels around recognized faces
- Displays the annotated image in a live window (press `q` to quit)

## Demo

```
$ python face_rec.py
['Yash', 'Unknown']
```

## Tech Stack

- **Python 3.8+**
- **OpenCV** — image processing and display
- **face_recognition** (dlib-based) — face encoding and comparison
- **NumPy** — array operations for distance calculations

## Project Structure

```
FACE_RECOGNITION/
├── face_rec.py          # Main recognition script
├── faces/               # Directory of known face images (.jpg/.png)
│   ├── yash.jpg
│   └── ...
├── test.jpg             # Test image to run recognition on
├── requirements.txt
├── .gitignore
└── README.md
```

## Setup

### Prerequisites

- Python 3.8 or higher
- CMake (required for dlib compilation)

### Installation

```bash
# Clone the repo
git clone https://github.com/YASH-1507/FACE_RECOGNITION.git
cd FACE_RECOGNITION

# Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Usage

1. Add known face images (`.jpg` or `.png`) to the `faces/` directory. The filename (without extension) becomes the label.

2. Place the image you want to test as `test.jpg` in the project root.

3. Run:
```bash
python face_rec.py
```

4. A window will display the image with recognized faces labelled. Press `q` to close.

## How It Works

1. **Encoding phase** — iterates through `faces/` and generates a 128-dimensional face encoding for each image using dlib's ResNet model
2. **Detection phase** — locates all face bounding boxes in the test image using HOG-based detection
3. **Comparison phase** — computes Euclidean distance between each detected face and all known encodings, picking the closest match
4. **Display phase** — draws rectangles and name labels on the image using OpenCV

## Limitations

- Assumes exactly one face per image in the `faces/` directory
- No error handling if a face isn't detected in a reference image
- Runs on a single static image (no webcam/video stream support yet)

## Future Improvements

- [ ] Add webcam real-time recognition
- [ ] Handle multiple faces per reference image
- [ ] Add confidence threshold filtering
- [ ] Implement a simple CLI for image path input
- [ ] Add logging instead of print statements

## License

This project is for educational purposes.
