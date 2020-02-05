# FarsiOCR
An OCR application for Farsi/ Persian documents.
This OCR application uses open source text recognition [Tesseract 4.1](https://github.com/tesseract-ocr/tesseract/wiki) and Python3.

Preprocessing is applied to each image before using `tesseract`. This is done to improve the performance of tesseract and also fix the rotation angle of the image (if needed). After converting the image to a `txt` file, the quality of ocr can be measured using the Levenshtein distance metric (By putting original.docx of the intended image into Data directory). 

## Installation
1. Install Tesseract

You can either install [Tesseract](https://github.com/tesseract-ocr/tesseract/wiki) via pre-built binary package or build it from source.

2. Install farsi language data for tesseract

[Download](https://github.com/tesseract-ocr/tessdata) language training data (fas.traineddata) and move the file to the following directory:
```linux
mv fas.traineddata /usr/local/share/tessdata
```
3. Install dependencies via `requirements.txt`
```cmd
pip3 install requirements.txt
```
## Installation via Docker
```docker
docker build docker build -t <image_name> .
docker run -—name <container_name> -it <image_name>
```
## How to use?
Copy your pdf or image files into the `Data` directory (a sample image in the Data directory is downloaded from the internet). 

Run the `src/ocr.py` and the results will be created in the `Output` directory.