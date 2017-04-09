

  <link type="text/css" rel="stylesheet" href="css/materialize.min.css"  media="screen,projection"/>
  <script type="text/javascript" src="https://code.jquery.com/jquery-2.1.1.min.js"></script>
  <script type="text/javascript" src="js/materialize.min.js"></script>
  <script>
    $(document).ready(function(){
      $('.collapsible').collapsible();
    });
   </script>
    
 <a href="https://eommer.github.io/EVEWebSite/" class="waves-effect waves-light btn-large">Home</a>
 <a href="https://eommer.github.io/EVEWebSite/gettingStarted.html" class="waves-effect waves-light btn-large">Getting started</a>
 <a href="doc/index.html" class="waves-effect waves-light btn-large">Documentation</a>
 
 
  <ul class="collapsible" data-collapsible="accordion">
    <li>
      <div class="collapsible-header">videoConverter usage</div>
      <div class="collapsible-body"><span markdown="1"> 
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
        </span></div>
    </li>
    <li>
      <div class="collapsible-header">subtitles usage</div>
      <div class="collapsible-body"><span markdown="1">
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
      </span></div>
    </li>
    <li>
      <div class="collapsible-header">Video usage</div>
      <div class="collapsible-body"><span markdown="1">
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
        </span></div>
    </li>
  </ul>
        
