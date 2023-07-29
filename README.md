# LSB Steganography Program

## Description
This is a C program for LSB (Least Significant Bit) Steganography. It allows you to hide a secret file within an image and retrieve the hidden file later. The program can be used for encoding (hiding) and decoding (extracting) the secret data from the image.

## Table of Contents
- [Usage](#usage)
- [Building the Program](#building-the-program)
- [Steganography Process](#steganography-process)
- [Supported Image Format](#supported-image-format)
-[Running Steps](#running-steps)
- [License](#license)
  

## Usage
To use the program, follow the instructions below:

### Encoding (Hiding a Secret File in an Image)
```bash
./lsb_steg -e <source_image> <secret_file> <output_image> <password>
```
- `<source_image>`: The source image (cover image) in which the secret file will be hidden.
- `<secret_file>`: The file you want to hide inside the image.
- `<output_image>`: The resulting steganographed image containing the hidden secret.
- `<password>`: A password to secure the hidden data (must be remembered for decoding).

### Decoding (Extracting the Hidden Secret from an Image)
```bash
./lsb_steg -d <steg_image> <output_secret_file> <image_format> <password>
```
- `<steg_image>`: The steganographed image that contains the hidden secret.
- `<output_secret_file>`: The file where the extracted secret will be saved.
- `<image_format>`: The format of the output image file (e.g., "BMP", "PNG", "JPEG", etc.).
- `<password>`: The password used during the encoding process.

## Building the Program
To build the program, make sure you have GCC (GNU Compiler Collection) installed on your system. Then, execute the following command in the terminal:

```bash
gcc -g -o lsb_steg main.c encode.c decode.c
```

## Steganography Process
The LSB Steganography process involves encoding the secret file into the image by manipulating the least significant bits of the image pixels. During decoding, the program extracts the secret data from the least significant bits of the steganographed image.

## Supported Image Format
The program currently supports BMP (Bitmap) image format for encoding and decoding. Ensure your image is in BMP format before using the program.
## Running steps


1. Open a terminal.

2. Navigate to the `lsb` directory where the `lsb_steg` program is located:
```bash
root@DESKTOP-GEG1S8J:~# cd ..
root@DESKTOP-GEG1S8J:/# cd home/
root@DESKTOP-GEG1S8J:/home# cd lsb/
```

3. To encode a secret file into an image, run the following command:
```bash
root@DESKTOP-GEG1S8J:/home/lsb# ./lsb_steg -e beautiful.bmp secret.txt
```
This command will encode the `secret.txt` file into the `beautiful.bmp` image and create a steganographed image named `stego_img.bmp`.

4. After encoding, you should see the following output:
```
INFO: Data encoding started
INFO: Encoded file Created as stego_img.bmp
INFO: read and validate is successful
INFO: opening the required files
INFO: Opened
INFO: Checking image capacity
width = 1024
height = 768
INFO: Source Image capacity = 2359296 bytes
INFO: Check capacity Done
=== ENCODING PROCEDURE STARTED ===
INFO: copying the header file from bmp file
INFO: Done
INFO: Encoding the magic string
INFO: Done
INFO: Encoding the file extension size
INFO: Done
INFO: Encoding the file extension
INFO: Done
INFO: Encoding the secret file size
INFO: Done
INFO: Encoding the file data
INFO: Done
INFO: Copying the remaining image file data
INFO: Done
==== ENCODING DONE SUCCESSFULLY ====
```

5. To decode the hidden secret from the steganographed image, run the following command:
```bash
root@DESKTOP-GEG1S8J:/home/lsb# ./lsb_steg -d stego_img.bmp dec.txt
```
This command will decode the hidden secret from `stego_img.bmp` and save it to a file named `dec.txt`.

6. After decoding, you should see the following output:
```
INFO: Data decoding started
INFO: read and validate is successful
INFO: Opening the required files
INFO: Opened
=== DECODING PROCEDURE STARTED ===
INFO: Decoding the magic string
INFO: The magic string is: #*
INFO: Done
INFO: Decoding the file extension size
INFO: Done
INFO: size of extension is: 4 bytes
INFO: Decoding the file extension
INFO: The decoded file extension is: .txt
INFO: Done
INFO: Decoding the secret file size
INFO: Done
INFO: size of the secret file is: 46 bytes
INFO: Decoding the file data
INFO: Done
==== DECODING DONE SUCCESSFULLY ====
```

7. The secret file `secret.txt` and the decoded file `dec.txt` should now contain the same content:
```bash
root@DESKTOP-GEG1S8J:/home/lsb# cat secret.txt
My password is SECRET ;
I love java
ctc 30lpa
root@DESKTOP-GEG1S8J:/home/lsb# cat dec.txt
My password is SECRET ;
I love java
ctc 30lpa
root@DESKTOP-GEG1S8J:/home/lsb#
```
![WhatsApp Image 2023-07-29 at 18 32 48](https://github.com/chaitanyasayee/LSB_Stegnography/assets/84325486/834ae717-2ca4-4618-a40a-b484ad1d84cb)

That's it! You have successfully used the LSB Steganography program to hide and extract a secret file within an image.

## License
This project is licensed under the [MIT License](LICENSE).


