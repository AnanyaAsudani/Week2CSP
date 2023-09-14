---
toc: true
comments: true
layout: post
title: Linux Code
description: This is ,y linux code, it will take a URL and make a file out of it
type: hacks
courses: { compsci: {week: 3} }
---

``` bash 
#!/bin/bash

# Check if wget is installed
if ! command -v wget &> /dev/null; then
  echo "wget is not installed. Please install it before using this script."
  exit 1
fi

# Create a directory to store downloaded files (if it doesn't exist)
download_dir="downloaded_files"
mkdir -p "$download_dir"

# Read the list of URLs from a file (one URL per line)
input_file="urls.txt"

# Check if the input file exists
if [ ! -f "$input_file" ]; then
  echo "Input file '$input_file' not found."
  exit 1
fi

# Loop through each URL in the input file and download the files
while read -r url; do
  # Extract the filename from the URL
  filename=$(basename "$url")
  
  # Download the file and save it to the download directory
  wget -q "$url" -P "$download_dir"
  
  # Check if the download was successful
  if [ $? -eq 0 ]; then
    echo "Downloaded: $filename"
  else
    echo "Failed to download: $filename"
  fi
done < "$input_file"

echo "Downloaded files are stored in the '$download_dir' directory."

exit 0

```