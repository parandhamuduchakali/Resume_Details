# Header Extraction from PDF Documents

## Overview
This project is focused on extracting headers and textual content from PDF documents. It leverages libraries like `spaCy`, `PyMuPDF`, `PyPDF2`, and `datefinder` to parse PDFs, identify headers based on font size and styles, and extract structured information from resumes and other documents.

## Features
- Extracts text from PDFs using `PyMuPDF` (`fitz`).
- Identifies headers based on font size and styles.
- Uses `spaCy` for Named Entity Recognition (NER) to extract names, emails, and phone numbers.
- Parses dates and durations for experience extraction.
- Converts structured text into JSON format.

## Installation
To run this project, install the required dependencies:

```sh
pip install spacy PyMuPDF PyPDF2 fuzzywuzzy datefinder numpy pandas dateparser pytesseract pdf2image
```

Additionally, download the `spaCy` large English model:

```sh
python -m spacy download en_core_web_lg
```

## Usage
### Extract Headers and Content from a PDF
1. Place your PDF files in the designated folder.
2. Run the script:
   ```sh
   python sprint_01_new_one_header_extraction.py
   ```
3. The extracted headers and text will be processed and printed or stored in structured format.

### Functions Overview
- **`fonts(doc, granularity=False)`**: Extracts font sizes and types from a PDF document.
- **`font_tags(font_counts, styles)`**: Assigns tags (e.g., `<h1>`, `<h2>`, `<p>`) based on font sizes.
- **`headers_para(doc, size_tag)`**: Extracts headers and text blocks based on font styles.
- **`get_name(text)`**: Extracts names using `spaCy`.
- **`get_email(text)`**: Extracts email addresses using regex.
- **`get_phone(text)`**: Extracts phone numbers using regex.
- **`get_total_experience(experience_list)`**: Calculates total work experience in months.

## Output
The extracted data is structured in JSON format:
```json
{
  "personal_details": {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "phone": "123-456-7890"
  },
  "work_experience": [
    {
      "company": "XYZ Corp",
      "duration": "Jan 2018 - Dec 2022",
      "role": "Software Engineer"
    }
  ],
  "education": "M.Sc. in Computer Science, ABC University"
}
```

## Limitations
- Accuracy depends on the formatting of the PDFs.
- Works best with structured documents like resumes and reports.

## Future Improvements
- Improve OCR capabilities for scanned PDFs.
- Enhance Named Entity Recognition (NER) models.
- Implement a web-based UI for easy PDF uploads and data extraction.

## License
This project is open-source and available under the MIT License.

---
Developed by **Your Name/Team**

