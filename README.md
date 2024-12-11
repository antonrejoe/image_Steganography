# Image Steganography Project

This project demonstrates how to hide one image inside another using **image steganography**. The hidden image is embedded in the least significant bits (LSBs) of the visible image, making it imperceptible to the naked eye. This repository contains the implementation of encoding and decoding processes.

---

## Table of Contents

- [Features](#features)
- [Principles](#principles)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Functions Explained](#functions-explained)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- Embed a hidden image within a visible image.
- Extract the hidden image from the encoded visible image.
- Works with `.png` and `.jpg` formats.
- Preserves the quality of the visible image.

---

## Principles

1. **Binary Representation of Pixels**:

   - Each pixel has three color channels (R, G, B) represented as 8-bit binary values.
   - The LSBs of the visible image are used to store the binary data of the hidden image.

2. **Embedding**:

   - The size of the hidden image is stored in the first pixel of the visible image.
   - Hidden image pixel values are split into chunks and embedded into the LSBs of visible image pixels.

3. **Extraction**:
   - The size of the hidden image is read from the first pixel of the encoded image.
   - Hidden image pixels are reconstructed from the LSBs of the encoded image pixels.

---

## Requirements

- Python 3.8+
- Libraries:
  - `Pillow` (for image processing)
  - `os` (for file handling)

Install the required libraries using:

```bash
pip install pillow
```

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/image-steganography.git
   ```
2. Navigate to the project directory:
   ```bash
   cd image-steganography
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

---

## Usage

### Encoding

1. Place the visible image and the hidden image in the `images/` directory.
2. Run the following code snippet:

   ```python
   from PIL import Image
   from your_module import encode

   img_visible_path = "images/women_image.png"
   img_hidden_path = "images/senior_image.jpg"
   output_path = "img/encoded_image.png"

   img_visible = Image.open(img_visible_path)
   img_hidden = Image.open(img_hidden_path)

   encoded_image = encode(img_visible, img_hidden)
   encoded_image.save(output_path)
   ```

### Decoding

1. Run the decoding script to extract the hidden image:

   ```python
   from PIL import Image
   from your_module import decode

   encoded_image_path = "img/encoded_image.png"
   output_path = "img/decoded_hidden_image.png"

   encoded_image = Image.open(encoded_image_path)

   decoded_image = decode(encoded_image)
   decoded_image.save(output_path)
   ```

2. The extracted hidden image will be saved in the `img/` directory.

---

## Project Structure

```
image-steganography/
├── images/              # Input images directory
├── img/                 # Output images directory
├── encode.py            # Encoding logic
├── decode.py            # Decoding logic
├── requirements.txt     # Required libraries
└── README.md            # Project documentation
```

---

## Functions Explained

### Encoding Functions

- **`rgb_to_binary(r, g, b)`**:
  Converts RGB values to 8-bit binary strings.

- **`get_binary_pixel_values(image, width, height)`**:
  Extracts binary pixel values of the hidden image.

- **`change_binary_values(img_visible, hidden_image_pixels, ...)`**:
  Embeds the hidden image pixels into the LSBs of the visible image pixels.

### Decoding Functions

- **`extract_hidden_pixels(image_copy, width_visible, height_visible, ...)`**:
  Extracts binary data from the LSBs of the visible image pixels.

- **`reconstruct_image(image_pixels, width, height)`**:
  Reconstructs the hidden image from binary data.

---

## Contributing

Contributions are welcome! To contribute:

1. Fork this repository.
2. Create a new branch:
   ```bash
   git checkout -b feature-branch-name
   ```
3. Commit your changes:
   ```bash
   git commit -m 'Add some feature'
   ```
4. Push to the branch:
   ```bash
   git push origin feature-branch-name
   ```
5. Open a pull request.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
