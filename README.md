# Image Compression Lab - LAB 10

A comprehensive implementation of **Huffman Coding** and **JPEG-like DCT Compression** algorithms with detailed metrics analysis and visualization.

##  Project Overview

This project demonstrates two fundamental image compression techniques:
1. **Huffman Coding** - Lossless compression
2. **DCT (Discrete Cosine Transform)** - Lossy compression (JPEG-like)

## Features

- ✅ Complete Huffman Coding implementation with encoding/decoding
- ✅ JPEG-like DCT compression with 8×8 block processing
- ✅ Comprehensive metrics calculation (CR, MSE, PSNR, Rate-Distortion)
- ✅ Visual comparison of original vs compressed images
- ✅ Rate-Distortion curve generation
- ✅ Side-by-side comparison with difference maps
- ✅ Multiple quality factor testing (10-90)

## 📋 Requirements

```bash
pip install numpy matplotlib pillow scipy
```

### Library Versions
- `numpy` - For numerical operations
- `matplotlib` - For visualization and plotting
- `pillow (PIL)` - For image loading
- `scipy` - For optimized DCT (optional but recommended)

## Quick Start

### Method 1: Jupyter Notebook (Recommended)

1. **Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/image-compression-lab.git
cd image-compression-lab
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Open Jupyter Notebook**
```bash
jupyter notebook LAB10_Image_Compression.ipynb
```

4. **Update image path** (Cell 5)
```python
image_path = 'your_image.jpg'
```

5. **Run all cells**
- Click `Cell` → `Run All`

### Method 2: Python Script

```bash
python image_compression_lab.py
```

##  Project Structure

```
image-compression-lab/
│
├── LAB10_Image_Compression.ipynb    # Main Jupyter notebook
├── image_compression_lab.py         # Python script version
├── README.md                         # This file
├── requirements.txt                  # Dependencies
│
├── images/                           # Sample images
│   └── lena.png                      # Test image
│
└── results/                          # Output files
    ├── compression_results.png       # Visual comparison
    └── rate_distortion_curve.png     # RD curve
```

## Algorithms Implemented

### 1. Huffman Coding (Lossless)

**How it works:**
- Builds frequency table of pixel values
- Creates binary tree based on frequencies
- Generates variable-length codes (frequent pixels = shorter codes)
- Encodes image using generated codes
- **Result**: Perfect reconstruction with moderate compression

**Key Features:**
- MSE = 0 (lossless)
- PSNR = ∞ (perfect quality)
- Compression Ratio: ~1.0-1.5x

### 2. DCT Compression (Lossy - JPEG-like)

**How it works:**
- Divides image into 8×8 blocks
- Applies 2D Discrete Cosine Transform to each block
- Quantizes DCT coefficients (lossy step)
- Stores quantized values
- **Decompression**: Dequantize → Inverse DCT

**Key Features:**
- Adjustable quality factor (1-100)
- Higher compression ratios (5-15x)
- Quality vs file size trade-off
- Uses standard JPEG quantization matrix

## Metrics Explained

### Compression Ratio (CR)
```
CR = Original Size / Compressed Size
```
- **Higher is better**
- CR = 10 means 10× smaller file

### Mean Squared Error (MSE)
```
MSE = mean((Original - Compressed)²)
```
- **Lower is better**
- MSE = 0 means perfect match

### Peak Signal-to-Noise Ratio (PSNR)
```
PSNR = 20 × log₁₀(255 / √MSE)
```
- **Higher is better**
- PSNR > 40 dB = Excellent quality
- PSNR 30-40 dB = Good quality
- PSNR < 30 dB = Noticeable degradation

### Rate-Distortion (RD)
- **Rate**: bits per pixel
- **Distortion**: MSE
- Shows compression efficiency

## 📸 Sample Results

### Huffman Coding
```
Compressed size: 180,000 bytes
Compression Ratio: 1.46
MSE: 0.0000
PSNR: ∞ dB
```

### DCT Compression (Quality = 50)
```
Compressed size: 25,000 bytes
Compression Ratio: 10.49
MSE: 45.23
PSNR: 35.57 dB
```

## Test Images

Recommended test images:
- **Lena** - Classic benchmark (512×512)
- **Cameraman** - Edge details
- **Peppers** - Natural colors
- Any natural photograph

Download from:
- [USC-SIPI Image Database](http://sipi.usc.edu/database/)
- Google Images: "lena test image 512x512"

## Visualizations

The project generates:

1. **Comparison Grid**
   - Original image
   - Huffman compressed
   - DCT compressed
   - Difference maps (error visualization)
   - Pixel value histograms

2. **Rate-Distortion Curve**
   - Shows quality vs compression trade-off
   - Tests 9 quality levels (10, 20, 30...90)
   - Compares Huffman vs DCT

## Customization

### Change DCT Quality
```python
quality_factor = 70  # Range: 1-100
# Higher = better quality, lower compression
# Lower = worse quality, higher compression
```

### Change Block Size
```python
dct = DCTCompression(block_size=16)  # Default: 8
```

### Test Custom Quality Levels
```python
qualities = [5, 15, 25, 50, 75, 95]
```

## 📖 Code Structure

### Classes

**`HuffmanNode`**
- Represents nodes in Huffman tree
- Stores symbol and frequency

**`HuffmanCoding`**
- `build_frequency_table()` - Count pixel frequencies
- `build_huffman_tree()` - Create binary tree
- `generate_codes()` - Generate variable-length codes
- `encode()` - Compress image
- `decode()` - Decompress image

**`DCTCompression`**
- `better_dct2d()` - 2D DCT transform
- `better_idct2d()` - 2D inverse DCT
- `compress()` - Apply DCT + quantization
- `decompress()` - Dequantize + inverse DCT

### Functions

- `calculate_compression_ratio()` - Compute CR
- `calculate_mse()` - Compute MSE
- `calculate_psnr()` - Compute PSNR
- `calculate_rd()` - Compute rate-distortion

## 🎯 Learning Outcomes

After completing this lab, you will understand:

1. ✅ How lossless compression works (Huffman)
2. ✅ How lossy compression works (DCT/JPEG)
3. ✅ Trade-off between quality and file size
4. ✅ Performance metrics (CR, MSE, PSNR)
5. ✅ Real-world compression techniques

## Troubleshooting

### Issue: "Module not found"
**Solution:**
```bash
pip install numpy matplotlib pillow scipy
```

### Issue: "Image file not found"
**Solution:** Update the `image_path` variable with correct path
```python
image_path = 'path/to/your/image.jpg'
```

### Issue: "scipy not available"
**Solution:** Code works without scipy (uses numpy fallback)
```bash
pip install scipy  # For faster DCT
```

## Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest features
- Submit pull requests

##License

This project is created for educational purposes as part of Image Processing Lab coursework.

## Author

Bushra
- Course: Image Processing Lab
- Lab: 10 - Image Compression
- Date: 2024

## Acknowledgments

- Test images from USC-SIPI Image Database
- JPEG quantization matrix from ISO/IEC 10918-1 standard
- Inspiration from various image processing textbooks

## Contact

For questions or issues, please open an issue in the GitHub repository.

##  References

1. Huffman, D. A. (1952). "A Method for the Construction of Minimum-Redundancy Codes"
2. Ahmed, N., Natarajan, T., & Rao, K. R. (1974). "Discrete Cosine Transform"
3. Wallace, G. K. (1992). "The JPEG Still Picture Compression Standard"
