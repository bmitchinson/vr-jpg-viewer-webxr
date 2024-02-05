<a-assets>
	<audio id="recording-asset" src="/audio.mp4" preload="auto"></audio>
	<img id="left-equir-asset" src="/left_equirectangular.jpg" />
	<img id="right-equir-asset" src="/right_equirectangular.jpg" />
</a-assets>

<a-sky id="left-skybox1" src="#left-equir-asset" stereo="eye:left"></a-sky>
<a-sky id="right-skybox1" src="#right-equir-asset" stereo="eye:right"></a-sky>
