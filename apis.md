
<head>
  <link type="text/css" rel="stylesheet" href="css/materialize.min.css"  media="screen,projection"/>
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
  <script type="text/javascript" src="https://code.jquery.com/jquery-2.1.1.min.js"></script>
  <script type="text/javascript" src="js/materialize.min.js"></script>
  <script>
    $(document).ready(function(){
      $('.collapsible').collapsible();
    });
   </script>
</head>
    
 <a href="https://eommer.github.io/EVEWebSite/" class="waves-effect waves-light btn-large">Home</a>
 <a href="https://eommer.github.io/EVEWebSite/gettingStarted.html" class="waves-effect waves-light btn-large">Getting started</a>
 <a href="doc/index.html" class="waves-effect waves-light btn-large">Documentation</a>
 <a href="api.html" class="waves-effect waves-light btn-large">Documentation</a>


<div class="row">
        <div class="col s12 m7">
          <div class="card small">
            <div class="card-image">
              <img src="nrecoSite.png">
              <span class="card-title"></span>
            </div>
<div class="card-content">
<span class="card-title activator grey-text text-darken-4">NReco VideoConverter<i class="material-icons right">more_vert</i></span>
      <p>API allowing to convert or concat video using ffmpeg</p>
    </div>
    <div class="card-reveal">
      <span class="card-title grey-text text-darken-4">NReco VideoConverter<i class="material-icons right">close</i></span>
<p>

	<div class="language-c# highlighter-rouge"><pre class="highlight"><code>	<span class="n">Video</span> <span class="n">vid1</span> <span class="p">=</span> <span class="k">new</span> <span class="nf">Video</span><span class="p">(</span><span class="s">@"C:/Program/name1.avi"</span><span class="p">,</span> <span class="n">name1</span><span class="p">,</span> <span class="m">20000</span><span class="p">);</span>
		<span class="n">Video</span> <span class="n">vid2</span> <span class="p">=</span> <span class="k">new</span> <span class="nf">Video</span><span class="p">(</span><span class="s">@"C:/Program/name2.avi"</span><span class="p">,</span> <span class="n">name2</span><span class="p">,</span> <span class="m">10000</span><span class="p">);</span>
		<span class="c1">//Convert video
	</span>	<span class="n">VideoConverter</span><span class="p">.</span><span class="nf">convertVideo</span><span class="p">(</span><span class="m">1920</span><span class="p">,</span> <span class="m">1080</span><span class="p">,</span> <span class="m">30</span><span class="p">,</span> <span class="s">"h264"</span><span class="p">,</span> <span class="s">"ac3"</span><span class="p">,</span> <span class="n">vid1</span><span class="p">);</span>
		<span class="n">VideoConverter</span><span class="p">.</span><span class="nf">convertVideo</span><span class="p">(</span><span class="m">1920</span><span class="p">,</span> <span class="m">1080</span><span class="p">,</span> <span class="m">30</span><span class="p">,</span> <span class="s">"h264"</span><span class="p">,</span> <span class="s">"ac3"</span><span class="p">,</span> <span class="n">vid2</span><span class="p">);</span>
		<span class="c1">//split video
	</span>	<span class="n">Video</span> <span class="n">vid1Part1</span> <span class="p">=</span> <span class="n">VideoConverter</span><span class="p">.</span><span class="nf">splitVideo</span><span class="p">(</span><span class="n">vid1</span><span class="p">,</span> <span class="m">1</span><span class="p">,</span> <span class="s">"00"</span><span class="p">,</span> <span class="s">"00"</span><span class="p">,</span> <span class="s">"00"</span><span class="p">,</span> <span class="s">"00"</span><span class="p">,</span> <span class="s">"00"</span><span class="p">,</span> <span class="s">"18"</span><span class="p">);</span>
		<span class="c1">//concatenate videos
	</span>	<span class="n">Video</span> <span class="n">vid3</span> <span class="p">=</span> <span class="n">VideoConverter</span><span class="p">.</span><span class="nf">concatTwoVideos</span><span class="p">(</span><span class="n">vid1</span><span class="p">,</span> <span class="n">vid2</span><span class="p">);</span>
	</code></pre>
	</div>

</p>
    </div>
            <div class="card-action">
              <a href="https://www.nrecosite.com/video_converter_net.aspx">Go to the site</a>
            </div>
          </div>
        </div>
</div>
      
<div class="row">
        <div class="col s12 m7">
          <div class="card small">
            <div class="card-image">
              <img src="nrecoSite.png">
              <span class="card-title"></span>
            </div>
<div class="card-content">
<span class="card-title activator grey-text text-darken-4">NReco Video Informations<i class="material-icons right">more_vert</i></span>
      <p>API allowing to get informations about a video</p>
    </div>
    <div class="card-reveal">
      <span class="card-title grey-text text-darken-4">NReco Video Informations<i class="material-icons right">close</i></span>
<p>

</p>
    </div>
            <div class="card-action">
              <a href="https://www.nrecosite.com/video_info_net.aspx">Go to the site</a>
            </div>
          </div>
        </div>
</div>

<div class="row">
        <div class="col s12 m7">
          <div class="card small">
            <div class="card-image">
              <img src="unosquare.jpg">
              <span class="card-title"></span>
            </div>
<div class="card-content">
<span class="card-title activator grey-text text-darken-4">Unosquare ffmediaElement<i class="material-icons right">more_vert</i></span>
      <p>API setting a mediaElement using ffmpeg</p>
    </div>
    <div class="card-reveal">
      <span class="card-title grey-text text-darken-4">Unosquare ffmediaElement<i class="material-icons right">close</i></span>
<p>

</p>
    </div>
            <div class="card-action">
              <a href="https://github.com/unosquare/ffmediaelement">Go to the site</a>
            </div>
          </div>
        </div>
</div>
        
