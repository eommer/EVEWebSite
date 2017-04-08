## Getting started (dev)

### Installing the project for visual Studio

  1. [Download](https://www.visualstudio.com/fr/downloads/?rr=https%3A%2F%2Fwww.google.fr%2F) and install Visual Studio 
  2. Clone the repisotory of the github
  3. Open EasyVideoEdition.sln with Visual Studio

### useful examples

**videoConverter usage**

```c#
	Video vid1 = new Video(@"C:/Program/name1.avi", name1, 20000);
	Video vid2 = new Video(@"C:/Program/name2.avi", name2, 10000);
	//Convert video
	VideoConverter.convertVideo(1920, 1080, 30, "h264", "ac3", vid1);
	VideoConverter.convertVideo(1920, 1080, 30, "h264", "ac3", vid2);
	//split video
	Video vid1Part1 = VideoConverter.splitVideo(vid1, 1, "00", "00", "00", "00", "00", "18");
	//concatenate videos
	Video vid3 = VideoConverter.concatTwoVideos(vid1, vid2);
```

[see documentation](doc/class_easy_video_edition_1_1_model_1_1_file_browser.html)

**subtitles usage**

```c#
	Video vid1 = new Video(@"C:/Program/name1.avi", name1, 20000);
	Subtitles subs = new Subtitles(vid1.filePath);
	//Read the srt file if it already exists one and add subtitles to the list
	subs.readSrtFile();
	//add a subtitle to the already existing list
	subs.addSubtitle("00:00:03,000", "00:00:07,000", "this is a subtitle example");
	//edit the first subtitle of the list
	subs.editSubtitle(0, "00:00:03,000", "00:00:07,000", "this is another subtitle example");
	//update or create the srt file
	subs.createSrtFile();
```

[see documentation](doc/class_easy_video_edition_1_1_model_1_1_file_browser.html)

**Video usage**

```c#
	Video vid1 = new Video(@"C:/Program/name1.avi", name1, 20000);
	//get the extention, the directory and the name of the video
	vid1.getExtension();
	vid1.getFileName();
	vid1.getDirectory();
	//show the duration of the video with appropriate unit
	Console.WriteLine(vid1.calDuration(vid1.duration));
	//show the size of the video with the appropriate unit
	Console.WriteLine(vid1.calcSize(vid1.size));
```

[see documentation](doc/class_easy_video_edition_1_1_model_1_1_file_browser.html)
