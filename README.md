# FarsiOCR
An OCR application for Farsi/ Persian documents.
This OCR application uses open source text recognition [Tesseract 4.1](https://github.com/tesseract-ocr/tesseract/wiki) and Python3.

Preprocessing is applied to each image before using `tesseract`. This is done to improve the performance of tesseract and also fix the rotation angle of the image (if needed). After converting the image to a `txt` file, the quality of ocr can be measured using the Levenshtein distance metric (By putting original.docx of the intended image into Data directory). 

## Installation
1. Install Tesseract

You can either install [Tesseract](https://github.com/tesseract-ocr/tesseract/wiki) via pre-built binary package or build it from source.

2. Install farsi language data for tesseract

[Download](https://github.com/tesseract-ocr/tessdata) language training data (fas.traineddata) and move the file to the following directory:
```shell script
mv fas.traineddata /usr/local/share/tessdata
```

3. Install poppler (PDF rendering library) for your OS
Ubuntu-based Linux: ```apt-get install -y poppler-utils```,
macOS: ```brew install poppler```,
Windows: download [poppler file for windows](https://blog.alivate.com.au/poppler-windows/) and install it


4. Install dependencies via `requirements.txt`
```shell script
pip install -r requirements.txt
```

## Installation via Docker
```shell script
docker build -t farsiocr .
docker run --name ocr -it --rm -v $PWD/data:/app/data -v $PWD/output:/app/output farsiocr
```
## How to use?
Copy your pdf or image files into the `data` directory (a sample image in the Data directory is downloaded from the internet). 

Run the `src/ocr.py` and the results will be created in the `output` directory.