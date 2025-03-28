# Rice Encoding and Decoding for Audio Files

## Overview

This project provides a comprehensive guide and tools for implementing Rice encoding and decoding techniques, specifically designed for audio files. Rice coding is an efficient method for compressing data by representing numbers in a specific format, which can significantly reduce file sizes.

## Installation

Before you start, ensure you have the necessary Python packages installed:

```
pip install tabulate matplotlib numpy
```

## Features

- Core Functions: Encode and decode data using custom Rice coding functions.
- Helper Functions: Convert between bits and bytes, ensure file equality, and test encoding/decoding processes.
- Practical Examples: Demonstrates encoding and decoding on sound files.
- Efficiency Measurement: Reports compression ratios for audio files.

## Usage

### Import Required Packages

```
import os
import struct
from tqdm.auto import tqdm
import numpy as np
import matplotlib.pyplot as plt
from tabulate import tabulate
```

### Encoding and Decoding Functions

#### Rice Encoding

```
def rice_encode(number, k) -> str:
    quotient = number >> k
    remainder = number & ((1 << k) - 1)
    return '1' * quotient + '0' + format(remainder, '0' + str(k) + 'b')
```

#### Rice Decoding

```
def rice_decode(code, k) -> int:
    quotient = code.find('0')
    remainder = int(code[quotient + 1:quotient + 1 + k], 2)
    return (quotient << k) + remainder
```

### Testing Functions

Ensure the correctness of encoding and decoding:

```
assert rice_decode(rice_encode(100, 3), 3) == 100
assert rice_decode(rice_encode(100, 3).ljust(100, '0'), 3) == 100
```

### Encode and Decode Audio Files

Create and decode encoded files with Rice coding at specified k values:

```
def encode_file_rice(input_file, output_file, k):
    # Encoding process abbreviated
    pass

def decode_file_rice(input_file, output_file, k):
    # Decoding process abbreviated
    pass
```

### Measuring Compression

Calculate the compression percentage achieved:

```
compression_percentage_4 = (1 - encoded_4_size / original_size) * 100
compression_percentage_2 = (1 - encoded_2_size / original_size) * 100
```

## Results

Visualize results through tables and graphs using tabulate and matplotlib.

```
table = tabulate(table_data, headers=["File", "Original Size", "Encoded (K = 4 bits)", "Encoded (K = 2 bits)", "% Compression (K = 4 bits)", "% Compression (K = 2 bits)"], tablefmt='html')
```

## Contribution

Feel free to fork this repository and contribute by submitting issues or pull requests. We welcome improvements and extensions to this Rice encoding project.

## License

This project is open-source and available under the MIT License. Please see the LICENSE file for more details.

For more detailed instructions, including code explanations and examples, refer to the project documentation. Enjoy discovering efficient audio file compression with Rice coding!
