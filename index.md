# Convert Teams and Zoom Transcripts to NVivo

This utility converts a Microsoft Teams or Zoom transcript to the [NVivo format](https://help-nv.qsrinternational.com/12/win/v12.1.108-d3ea61/Content/files/import-audio-video-transcripts.htm) so as to make coding and analysis as easy as possible. Click [here](converter.html) to go straight to the utility.

## Introduction

[Microsoft Teams](https://twitter.com/MicrosoftTeams) does surprisingly good automated transcription, as does [Zoom](https://zoom.us/); and these transcripts can be downloaded along with the corresponding recordings. 

This utility allows you to use these transcripts with [NVivo](https://www.qsrinternational.com/nvivo-qualitative-data-analysis-software/home), the popular qualitative analysis software. It's written in HTML and JavaScript so only requires your browser to run.

 NVivo doesn't allow you to code two transcript items at once, so this combines as many items by a single speaker as possible. And Teams transcription times aren't always aligned with the start of the recording, so this implements a 'time shift'.

## Instructions

These instructions are importing from Teams to Windows NVivo 12. Zoom and Mac users may need to adjust them for your own situation (and yes, the converter supports Zoom transcripts)

* Record your interview in Teams, creating a transcript 
* The video and transcript appear as entries in due course in the chat (**The transcript may take several hours to produce**)
* <img src="images/TeamsChat.png">
* On the video, click *...* and *Open in Microsoft Stream.* Scroll down to Details tab, and click *... Download video*.
* Optionally, if you want audio only, click on the downloaded video file to open in Quicktime; use *File - Export As - Audio Only* to get an m4a file
* import the M4A audio or MP4 video into NVivo - see [here](https://help-nv.qsrinternational.com/12/win/v12.1.108-d3ea61/Content/files/audio-and-videos.htm)

* On the transcript in the chat, click *... Download as .vtt* **Note:** You could also download a VTT transcript from Microsoft Stream---but that version doesn't have speaker names.  

* Use the [converter page here](converter.html) to convert that .vtt file to NVivo transcript format (whose file extension is .txt).
    
* Import that transcript into NVivo by opening the recording and clicking *Edit*, then *Import rows*. Use the options *One transcript row for each tab-delimited line*, *File includes header row*, and manually set the obvious field mappings as shown below (details blanked for privacy). There's more information [here](https://help-nv.qsrinternational.com/12/win/v12.1.108-d3ea61/Content/files/import-audio-video-transcripts.htm#Import_a_transcript):

* <img src="images/NVivoImport.png">

* Click OK to do the import. If NVivo pops up a dialog with *The timespan of one or more entries...*, click OK

* You'll see the transcript entries have '---' internally instead of paragraph endings (NVivo doesn't have a text transcript input format that supports both speaker identification and multiple paragraphs in a single transcript 'line'). Use *Edit tab - Find & Select - Replace* to replace instances of "---" with "^p^p" (a blank line): 

* <img src="images/NVivoReplace.png">

* Click *Replace all*. It takes a while and looks a bit odd, but it works. Click OK to the *Replaced Instances* dialog and you're done. 

## Changing timestamps 

Sometimes (usually?) the timings on the transcript are a few seconds different from those in the recording. NVivo doesn't seem to have an easy way to correct that, so we've implemented one in the script here. 

To fix the timestamps, before doing the conversion, 
* Open the VTT transcript file in a text editor, and the M4A file in a normal viewer. 
* Find a statement that’s identifiable in both (maybe the first thing said) and note the timings T<sub>vtt</sub> and T<sub>m4a</sub> for that statement. 
* Then the timeshift value should be (T<sub>m4a</sub> - T<sub>vtt</sub>), converted to seconds. It can often be negative. 
* Put that value in the *Time shift (advanced)* box.

## Removing interviewer encouragements

You may also find in an interview that there are a lot of 'ums' and 'yes' that break up the flow.

To fix that, just tick the *Filter out short phrases* box on the coverter page. It removes all interjections less than 10 words long. To check you've not missed anything important, the converter shows the list of all words filtered out.

## Removing a transcript in NVivo to try again

You can delete the transcript entries in NVivo using (in Edit mode) *Click on an item in the left hand column - Right click Select All - Right click Delete*.  Or, if you've just done the import, just use *Undo* a couple of times.

## Credits

Thanks go to [Steve Wright, NVivo and Atlas TI guru](https://caqdasblog.wordpress.com/), who introduced us to advanced NVivo techniques and to automated coding. And thanks to [Tim Ellis](https://github.com/TimEllis), who created the first version of this tool.
