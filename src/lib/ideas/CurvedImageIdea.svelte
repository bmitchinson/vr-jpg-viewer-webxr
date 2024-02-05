<a-assets>
	<img id="blur-sky-asset" src="/skybox_sample_blur.jpg" />
	<img id="left-strip-asset" src="/left_no_boundaries.jpg" />
	<img id="right-strip-asset" src="/right_no_boundaries.jpg" />
</a-assets>

<a-sky id="blur-sky" src="#blur-sky-asset"></a-sky>

<a-curvedimage
	src="#left-strip-asset"
	stereo="eye:left"
	height="10"
	radius="8"
	theta-length="360"
	position="0 2 0"
></a-curvedimage>
<a-curvedimage
	src="#right-strip-asset"
	stereo="eye:right"
	height="10"
	radius="8"
	theta-length="360"
	position="0 2 0"
></a-curvedimage>
