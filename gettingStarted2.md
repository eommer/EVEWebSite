
[Home](index.md)   |    [Documentation](doc/index.html)   |    [APIs](apis.md) 

<button>Test</button>

## Getting started (dev)

### Installing the project for visual Studio

  1. [Download](https://www.visualstudio.com/fr/downloads/?rr=https%3A%2F%2Fwww.google.fr%2F) and install Visual Studio 
  2. Clone the repisotory of the github
  3. Open EasyVideoEdition.sln with Visual Studio
  
### useful examples

***

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

***

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

```c#
	/* Initializing the process */
            Process process = new Process();
            process.StartInfo.RedirectStandardOutput = true;
            process.StartInfo.RedirectStandardError = true;
            process.StartInfo.FileName = "ffmpeg";
            process.StartInfo.UseShellExecute = false;
            process.StartInfo.CreateNoWindow = true;
            
            process.StartInfo.Arguments = "-i " + pathVideo + " -i " + pathsrt + " -map 0 -map 1 -c copy output.mkv";
```

[see documentation](doc/class_easy_video_edition_1_1_model_1_1_file_browser.html)

***

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

```cs
	public void exportVideoStart(int width, int height, int frameRate, string outputVideoCodec, string outputAudioCodec, IEnumerator<StoryBoardElement> videoList, String savePath)
```

```cs
	List<Video> videoArray = new List<Video>();
	//-------------------------
	//Convertion of the video file 
	while (videoList.MoveNext())
	{
	    StoryBoardElement ele = videoList.Current;
	    Video v;
	    if (ele.fileType.Equals("Video"))
	    {
	    	/* Split the storyBoard element if it must be */
		if(ele.hasToBeSplit == true)
		{
			
		    v = splitVideo((Video)ele.file, ele.numPart, ele.startTimeInSource, ele.endTimeInSource); //extract the part from the original video

		}
		else
		{
		    v = (Video)ele.file;
		}

		convertVideo(width, height, frameRate, outputVideoCodec, outputAudioCodec, v);
		//update of the path in the file list
		ele.filePath = v.filePath;
		_offsetConvertProgress += v.duration;
		videoArray.Add(v);
	    }
	}
	videoList.Reset();
	//End of convertion
	//-------------------------

	Video FINAL = concatVideoArray(videoArray, width, height, frameRate, outputVideoCodec, savePath);
```

***

**Double Slider**


```xml
	<UserControl.Resources>
        <ControlTemplate x:Key="simpleSlider" TargetType="{x:Type Slider}">
            <Border SnapsToDevicePixels="true" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}">
                <Grid>
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto"/>
                        <RowDefinition Height="Auto" MinHeight="{TemplateBinding MinHeight}"/>
                        <RowDefinition Height="Auto"/>
                    </Grid.RowDefinitions>

                    <Rectangle x:Name="PART_SelectionRange"/>

                    <Track x:Name="PART_Track" Grid.Row="1">
                        <Track.Thumb>
                            <Thumb x:Name="Thumb">
                                <Thumb.Template>
                                    <ControlTemplate TargetType="Thumb">
                                        <Rectangle Fill="Black" 
                                                   Stroke="#656767"
                                                   StrokeThickness="0.5" 
                                                   Width="7"
                                                   Height="55"
                                                   SnapsToDevicePixels="True"
                                                  RadiusX="10" RadiusY="2"/>
                                    </ControlTemplate>
                                </Thumb.Template>
                            </Thumb>
                        </Track.Thumb>
                    </Track>
                </Grid>
            </Border>
        </ControlTemplate>

    </UserControl.Resources>
    <Grid VerticalAlignment="Center">
        <Rectangle Fill="#FFAFB4B3" VerticalAlignment="Center" Height="45" Margin="5,0,5,0" Stroke="#3E4145"/>

        <Slider x:Name="LowerSlider"
                Minimum="{Binding ElementName=root, Path=Minimum}"
                Maximum="{Binding ElementName=root, Path=Maximum}"
                Value="{Binding ElementName=root, Path=LowerValue, Mode=TwoWay}"
                Template="{StaticResource simpleSlider}"
                Margin="0,0,7,0"
                />

        <Slider x:Name="UpperSlider"
                Minimum="{Binding ElementName=root, Path=Minimum}"
                Maximum="{Binding ElementName=root, Path=Maximum}"
                Value="{Binding ElementName=root, Path=UpperValue, Mode=TwoWay}"
                Template="{StaticResource simpleSlider}"
                Margin="7,0,0,0"
                />
    </Grid>
```
***
*Functions*
```cs
    public partial class DoubleSlider : UserControl
    {
        public DoubleSlider()
        {
            InitializeComponent();

            this.Loaded += Slider_Loaded;
        }

        void Slider_Loaded(object sender, RoutedEventArgs e)
        {
            LowerSlider.ValueChanged += LowerSlider_ValueChanged;
            UpperSlider.ValueChanged += UpperSlider_ValueChanged;
        }

        /// <summary>
        /// Updates value of the right thumb to both sliders composing the doubleSlider
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void LowerSlider_ValueChanged(object sender, RoutedPropertyChangedEventArgs<double> e)
        {
            UpperSlider.Value = Math.Max(UpperSlider.Value, LowerSlider.Value);
        }

        /// <summary>
        /// Updates value of the left thumb to both sliders composing the doubleSlider
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void UpperSlider_ValueChanged(object sender, RoutedPropertyChangedEventArgs<double> e)
        {
            LowerSlider.Value = Math.Min(UpperSlider.Value, LowerSlider.Value);
        }

        /// <summary>
        /// Minimum is the lowest value the left thumb can have
        /// </summary>
        public double Minimum
        {
            get { return (double)GetValue(MinimumProperty); }
            set { SetValue(MinimumProperty, value); }
        }

        public static readonly DependencyProperty MinimumProperty =
            DependencyProperty.Register("Minimum", typeof(double), typeof(DoubleSlider), new UIPropertyMetadata(0d));

        /// <summary>
        /// LowerValue is the value of the left thumb, between Minimum and Maximum (defined in other functions)
        /// </summary>
        public double LowerValue
        {
            get { return (double)GetValue(LowerValueProperty); }
            set { SetValue(LowerValueProperty, value); }
        }

        public static readonly DependencyProperty LowerValueProperty =
            DependencyProperty.Register("LowerValue", typeof(double), typeof(DoubleSlider), new UIPropertyMetadata(0d));


        /// <summary>
        /// UpperValue is the value of the right thumb, between Minimum and Maximum (defined in other functions)
        /// </summary>
        public double UpperValue
        {
            get { return (double)GetValue(UpperValueProperty); }
            set { SetValue(UpperValueProperty, value); }
        }

        public static readonly DependencyProperty UpperValueProperty =
            DependencyProperty.Register("UpperValue", typeof(double), typeof(DoubleSlider), new UIPropertyMetadata(0d));

        /// <summary>
        /// Maximum is the highest value the right thumb can have
        /// </summary>
        public double Maximum
        {
            get { return (double)GetValue(MaximumProperty); }
            set { SetValue(MaximumProperty, value); }
        }

        public static readonly DependencyProperty MaximumProperty =
            DependencyProperty.Register("Maximum", typeof(double), typeof(DoubleSlider), new UIPropertyMetadata(1d));
    }

```

***
**ResourceDictionnary**

```xml
<Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <ResourceDictionary Source="Dictionnary/Instructions/InstructionsButtonShown.xaml"/>
		<ResourceDictionary Source="Dictionnary/Instructions/InstructionsButtonHidden.xaml"/>
				[...]
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
</Application.Resources>
```

