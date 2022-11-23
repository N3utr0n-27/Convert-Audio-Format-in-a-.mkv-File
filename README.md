# Convert-Audio-Format-in-a-.mkv-File
If you have a video file (.mkv) that doesn't work on your TV, you can check what audio format is used in the mkv file. DTS for example, is not supported by LG TVs and therefore you need to convert it to another audio format. The following steps show you how to check, extract, convert and mix it back together in order to watch your movie or show on your TV.
- Check Audio Format
- Extract Audio Track
- Convert Audio Track
- Mix Converted Audio with Video

## Check Audio Format
`Tool: MediaInfo` Download: [MediaInfo](https://mediaarea.net/en/MediaInfo/Download/Windows)
1. Open MediaInfo
2. Open a File or a Folder with File > Open > File/Folder > Choose File/Folder
3. Change View to Sheet to have a quick overview
4. The Audio Format used in the mkv File should be displayed in the Audio_Format_List column `e.g. DTS, AC-3, ...`

## Extract Audio Track
`Tool: gMKVExtractGUI` Download: [gMKVExtractGUI](https://sourceforge.net/projects/gmkvextractgui/)
1. Open gMKVExtractGUI
2. Right click the big white input field > Add Input file(s) > Choose File(s)
3. Select the audio track that needs to be converted `e.g. DTS, ger (search for audio format and language)`
4. Select Use Source in the Output Directory
5. Press Extract

## Convert Audio Track
`Tool: UsEac3To` Download: [UsEac3To](https://www.videohelp.com/software/eac3to)
1. Open UsEac3To
2. Load the extracted Audio Track with the Input File button on the right > Choose File
3. Choose ac3 in the second drop down in the Track Input and Output format section and press Add
4. Press RUN CL to convert the Audio Track

## Mix Converted Audio with Video
`Tool: MKVToolNix GUI` Download: [MKVToolNix GUI](https://www.videohelp.com/software/MKVToolNix)
1. Open MKVToolNix GUI
2. In the Multiplexer Tab load the source File with Right Click the source File field > Add File > Choose the original mkv File
3. Add another File > Choose the converted Audio Track `.ac3`
4. In the field below you can see the detailed Files / Codecs
5. Remove the selection on the Audio Tracks you don't want `e.g. DTS`
6. Press Start Multiplexer in the bottom middle

#### AUX
After the Mix, the new video file is created and has a file name ending `" (1)"`
You can use the following PowerShell Script to remove that ending:
```powershell
# Change the FOLDERPATH below according to your folder where your files are!
cd FOLDERPATH
get-childitem *.mkv | foreach { rename-item $_ $_.Name.Replace(" (1)", "") }
```
