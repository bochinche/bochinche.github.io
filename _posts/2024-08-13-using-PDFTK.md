---
layout: post
title:  "Merge two PDF files containing even and odd pages of a document"
date:   2024-08-13 08:00:00 +0100
categories: linux it PDF osx 
---

## Installing PDFTK

### on osx
```bash
brew install pdftk-java
```
### on linux 
```bash
sudo apt-get install pdftk
```
## Collating Pages (normal order)

```bash
pdftk A=odd.pdf B=even.pdf shuffle A B output collated.pdf
```
## Collating Pages (reversing the order of the even pages)

```bash
pdftk A=odd.pdf B=even.pdf shuffle A Bend-1 output collated_pages.pdf
```

## Creating a bash script

1. Edit the script with VIM or nano, depeding on your preference

```bash
vim $HOME/bin/interleave-pdfs.sh
```

2. Copy the following text

```bash
#!/bin/bash

# Check if the correct number of arguments is provided
if [ "$#" -ne 2 ]; then
    echo "Usage: $0 <odd_pages_pdf> <even_pages_pdf>"
    exit 1
fi

# Assign input arguments to variables
odd_pdf=$1
even_pdf=$2

# Output file name
output_pdf="interleaved_PFF.pdf"

# Run the pdftk command to shuffle the pages
pdftk A="$odd_pdf" B="$even_pdf" shuffle A Bend-1 output "$output_pdf"

# Check if pdftk command was successful
if [ $? -eq 0 ]; then
    echo "Successfully created $output_pdf"
else
    echo "Failed to create $output_pdf"
    exit 1
fi
```
3. Make the file executable

```bash
chmod +x $HOME/bin/interlacePDFs.sh
```





## Links 
- [Merge two PDF files containing even and odd pages of a book](https://superuser.com/questions/516612/merge-two-pdf-files-containing-even-and-odd-pages-of-a-book)