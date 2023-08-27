import pytesseract
from pdf2image import convert_from_path

# Path to the Tesseract executable
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'  # Update with your Tesseract path

# Path to the scanned PDF
pdf_path = 'path/to/your/scanned.pdf'

# Convert PDF to images
images = convert_from_path(pdf_path)

# Extract text from images using OCR
extracted_text = []
for i, image in enumerate(images):
    text = pytesseract.image_to_string(image, lang='eng')
    extracted_text.append(text)

# Save extracted text to a text file
with open('extracted_text.txt', 'w') as f:
    f.writelines(extracted_text)

print('Text extracted and saved to extracted_text.txt')
