# Subtitles Transformation

## Goal

Programmatically add subtitles to video (MP4) from CSV transcripts and timestamps

## Prerequisites
- Python 3.x
- Required Python packages: `os`, `pysrt`, `csv`, `moviepy.editor`

## Cloning
To clone the repository on local machine, run:
```
git clone https://github.com/uliza/Subtitles.git
```

## Running Locally 

1. change input and output folder path 
2. add an MP4 file to add subtitles to and a subtitles .srt file with the same name to the input folder 
2. cd into the Subtitles folder and run:

```
python3 srt_to_mp4.py
```

## Code

The project is structured as follows:

- `pdf_to_csv.py` contains the main code to turn PDF/DOCX files into CSV using various different formatting changes needed for the subtitles work
- `csv_to_srt.py` contains the main project code to generate a subtitles .srt file from the relevant CSV file
- `srt_to_mp4.py` contains the main project code to take in the input, create subtitle clips, perform formatting changes, and burns the subtiltes before writing out the outout video.
- `/input` contains video input .mp4 files and their respective subtitles .srt files with same name
- `/inputcsv` contains PDF/DOCX files that need to be turned into CSV files using Parsing work
- `/inputsrt` contains CSV files that need to be turned into SRT files csv_to_srt.py
- `/output` contains output video .mp4 files with subtitles added
- `/outputcsv` contains output CSV files generated from Parsing work(input of PDF/DOCX files)
- `/outputsrt` contains output SRT files generated from CSV to SRT work(input of CSV files)


## Customization

### Formatting
To change the formatting of the subtitles, change the options on the following lines for both the English clip and the non-English TextClip: 
```
        # Creating subtitle TextClips with some attributes(duration, start time, styling)
        other_language_text_clip = TextClip(''.join(other_language.splitlines()), fontsize=22, font="Arial", color=non_eng_language_color, bg_color = 'black',size=size, method='caption').set_start(start_time).set_duration(subtitle_duration)
        english_clip = TextClip(''.join(english.splitlines()), fontsize=22, font="STIXGeneral-Italic", color="white", bg_color = 'black',size=size, method='caption').set_start(start_time).set_duration(subtitle_duration)
```

The following can be changed: 
- fontsize (Font Size of the subtitle)
- font (Font of the subtitle. Currently set to Arial. Availaible fonts can be viewed by running `print(TextClip.list('font')`)
- color (Color of the subtitle. For Non-english languages, the colors are currently red, yellow, and cyan. Availaible colors can be viewed by running `print(TextClip.list('color')`)
- bg_color (Background color of the subtitle box. Availaible colors can be viewed by running `print(TextClip.list('color')`)

### Layouts and Positions
To change the layout and positions of the subtitles, change the following:
```
        # Positioning and handling the subtitle for the non-English language
        subtitle_clips.append(other_language_text_clip.set_position(("center", "top")))

        # Positioning and handling the subtitle for the English language (right below the non-English TextClip)
        subtitle_clips.append(english_clip.set_position(("center", "bottom")))
```
The position can be at bottom, top, etc. 

To update the width of the subtitle box, multipy `video_width` by a number [0,1] in the following
```
        # Size of the subtitle picture/box in pixels (height is auto-determined/None)
        size=(video_width, None) 
```
## Creating just a Sample
srt_to_mp4.py
- Comment out actual writing frame row: row 105
- Comment out actual video in loading input video and opening subtitles file row : row 90
- Uncomment out Preview video without writing frame row : row 102
- uncomment Loading input video and opening subtitles file row : row 92 

## Toggling Removing Speakers of English or Non-English Text
** In csv_to_srt.py**

To remove speaker for the English text:
1. uncomment the section `Removing Speaker for English Text`


To remove speaker for the Non-English text:
1. uncomment the section `Removing Speaker for Non-English Text`

