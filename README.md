
# Optimized Steganography – Huffman + LSB-Based File Hiding in BMP Images

A web-based application (with a C-powered backend) to hide any type of file securely inside BMP images using Huffman compression and Least Significant Bit (LSB) steganography.

> Developed as part of the MCA/MSc IT PBL Project – Team StegnoBits

---

## Features

- Hide any file (text, image, PDF, etc.) inside 24-bit BMP images
- Huffman compression for better storage efficiency
- Accurate decoding and original file recovery without loss
- Web interface built using Streamlit (optional)
- Auto-detects and preserves original file format
- No external C libraries – fully custom compression and steganography logic

---

## Requirements

### If you're using the CLI version:
- C compiler (GCC / Clang / MinGW)
- Standard C libraries

### If you're using the Web UI:
- Python 3.7+
- Streamlit
- Emscripten (if compiling C to WebAssembly)
- requirements.txt (includes Python dependencies)

---

## Setup Instructions

### Compile the C Code
```bash
# For CLI use
gcc main.c huffman.c steganography.c -o stegano_app
```
> Replace file names with actual ones if different.

### (Optional) Run Web Application
```bash
pip install -r requirements.txt
streamlit run app.py
```

---

## How It Works

### Encoding Flow
1. Read the input (secret) file
2. Compress it using Huffman Coding
3. Embed:
   - File size
   - Frequency table
   - Compressed binary data
   into the LSBs of the BMP cover image
4. Save the output as a new stego BMP image

### Decoding Flow
1. Load the stego image
2. Extract file size and frequency table
3. Reconstruct Huffman tree
4. Decode and save the original secret file

---

## Usage – CLI Version

```bash
# Run the executable
./stegano_app

# Follow on-screen prompts to:
# 1. Select BMP cover image
# 2. Choose secret file to hide
# 3. Encode / Decode as required
```

---

## Usage – Web Version

1. Open your browser to the address shown (usually http://localhost:8501)
2. To Encode:
   - Upload BMP cover image
   - Upload secret file
   - Click “Encode”
   - Download stego image
3. To Decode:
   - Upload stego image
   - Click “Decode”
   - Download extracted file

---

## Notes

- BMP image must be 24-bit, uncompressed
- Secret file size must fit within image capacity (checked automatically)
- Huffman compression improves embedding efficiency
- No external C libraries used (pure standard C)

---

## Troubleshooting

- Check file types: must use BMP images
- Encoding fails? Try using a larger image
- Verify permissions for writing files
- If using web version, ensure C executable is present and callable

---

## Team

| Name             | Role                            |
|------------------|----------------------------------|
| Aditya Shrestha  | Huffman logic, CLI integration   |
| Khushi Panwar    | LSB logic, BMP file handling     |
| Pranjal Kala     | Bit-level operations, testing    |

---

## References

- [GeeksforGeeks – Huffman Coding](https://www.geeksforgeeks.org/huffman-coding-greedy-algo-3/)
- [ScienceDirect – Steganography](https://www.sciencedirect.com/topics/computer-science/steganography)
- [BMP File Format Docs](https://en.wikipedia.org/wiki/BMP_file_format)
