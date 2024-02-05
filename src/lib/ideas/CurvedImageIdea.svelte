<script>
	let height = 10;
	let radius = 8;
	let thetaLength = 360;
	let thetaStart = 0;
	let position = '0 2 0';
	let animation = 'property: rotation; to: 0 360 0; loop: true; dur: 50000; easing: linear';
</script>

<a-assets>
	<img id="blur-sky-asset" src="/skybox_sample_blur.jpg" />
	<img id="left-strip-asset" src="/left_no_boundaries.jpg" />
	<img id="right-strip-asset" src="/right_no_boundaries.jpg" />
</a-assets>

<a-sky id="blur-sky" src="#blur-sky-asset"></a-sky>

<a-curvedimage
	src="#left-strip-asset"
	stereo="eye:left"
	{height}
	{radius}
	theta-length={thetaLength}
	theta-start={thetaStart}
	{position}
	{animation}
></a-curvedimage>
<a-curvedimage
	src="#right-strip-asset"
	stereo="eye:right"
	{height}
	{radius}
	theta-length={thetaLength}
	theta-start={thetaStart}
	{position}
	{animation}
></a-curvedimage>
