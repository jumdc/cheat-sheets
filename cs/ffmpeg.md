# ffmpeg

- [ffmpeg](#ffmpeg)
- [Convert videos to the appropriate format](#convert-videos-to-the-appropriate-format)
- [Information about video input ](#information-about-video-input-)
- [Processing frames ](#processing-frames-)
  - [Trim from video frames number ](#trim-from-video-frames-number-)
  - [Trim from a start time and an end time ](#trim-from-a-start-time-and-an-end-time-)
- [Processing audio ](#processing-audio-)
  - [Various audio tracks ](#various-audio-tracks-)
    - [Check the audio tracks](#check-the-audio-tracks)
    - [Extract as wav](#extract-as-wav)
    - [For the following track :](#for-the-following-track-)
  - [Raw extract ](#raw-extract-)


# Convert videos to the appropriate format

```bash
ffmpeg -i input.vob -vf format=yuv420p output.mp4 
```


# Information about video input <a name="info"></a>
**Ffprobe** gathers information from multimedia streams. 
```{bash}
$ ffprobe \
  -i input.mp4 #input file
```
This command allows to determine how many audio tracks the input contains. 
Check for the the line containing : 'Stream' and 'Audio'.

# Processing frames <a name="frames"></a>
## Trim from video frames number <a name="trimframe"></a>
```{bash}
$ ffmpeg \
  -i 13025.mp4 #input \
  -filter_complex 'trim=start_frame=100:end_frame=110,setpts=PTS-STARTPTS' #trim \
  -an  # audio disable \
  %04d.png #output in the form of a serie of digit \
```

## Trim from a start time and an end time <a name="trimtime"></a>
```{bash}
$ ffmpeg \
  -i 13025.mp4 #input \
  -ss HH:MM:SS #start of the cut \
  -to HH:MM:SS #end of the cut \
  -an # disable audio \
  %d.png #output
```

```{bash}
$ ffmpeg \
  -i 13025.mp4 \
  -ss 00:00:53.29 \
  -to 00:01:01.18 \
  -an \
  -start_number 98 #number to start the output \
  13025/%04d.png 
```
# Processing audio <a name="audio"></a>
## Various audio tracks <a name="basicaudio"></a>
### Check the audio tracks 
```{bash}
$ ffprobe \
  -i input.mp4 #input file
```
This command allows to determine how many audio tracks the input contains. 
Check for the the line containing : 'Stream' and 'Audio'.

### Extract as wav
```{bash}
$ ffmpeg \
  -i video.mp4 \
  -map 0:a:0 #focus on a specific thing \
  track.wav #save as uncompressed wav format
```
more on -map : 
*0*, focus on the first input file we have (only have 1 here), *a* for audio, *0* represents the first track. 

### For the following track : 
```{bash}
$ ffmpeg \
  -i video.mp4 \
  -map 0:a:1 #focus on a specific thing \
  track.wav #save as uncompressed wav format
```
## Raw extract <a name="rawextract"></a>
Check the original encoding of the audio stream. 
Example : 
```{bash}
$ ffprobe -i input 
Stream #0:1(eng): Audio: aac (LC) (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 189 kb/s (default)
```
The original encoding is : *aac*
```{bash}
$ ffmpeg \
  -i video.mp4 \
  -map 0:a:1 #focus on a specific thing \
  -c copy  #c is for codec
  track.aac #save as uncompressed wav format
```
more on -c : 
We take the original input and copy it straight to the output


