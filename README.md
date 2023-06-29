# Subtitles Transformation

## Goal

Programmatically add subtitles to video (MP4) from CSV transcripts and timestamps

## Prerequisites
- Python 3.x
- Required Python packages: `os`, `pysrt`, `csv`, `moviepy.editor`

## Cloning
To clone the repository on local machine, run:
```
git clone https://github.com/farooqashar/Subtitles.git
```

## Running Locally 

1. change input and output folder path 
2. add an MP4 file to add subtitles to and a subtitles .srt file with the same name to the input folder 
2. cd into the Subtitles folder and run:

```
python3 final.py
```

## Code

The project is structured as follows:

- `final.py` contains the main project code to take in the input, create subtitle clips, perform formatting changes, and burns the subtiltes before writing out the outout video.
- `finalcsv.py` contains the main code to turn PDF/DOCX files into CSV using various different formatting changes needed for the subtitles work
- `/input` contains video input .mp4 files and their respective subtitles .srt files with same name
- `/inputcsv` contains PDF/DOCX files that need to be turned into CSV files using Parsing work
- `/output` contains output video .mp4 files with subtitles added
- `/outputcsv` contains output CSV files generated from Parsing work(input of PDF/DOCX files)
- `SRT.py` contains the main project code to generate a subtitles .srt file from the relevant CSV file
