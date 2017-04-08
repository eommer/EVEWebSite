## Getting started (dev)

### Installing the project for visual Studio

  1. [Download](https://www.visualstudio.com/fr/downloads/?rr=https%3A%2F%2Fwww.google.fr%2F) and install Visual Studio 
  2. Clone the repisotory of the github
  3. Open EasyVideoEdition.sln with Visual Studio

### Installing the project for visual Studio

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
