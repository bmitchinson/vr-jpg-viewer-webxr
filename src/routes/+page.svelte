<script>
</script>

<svelte:head>
  <script src="https://aframe.io/releases/1.5.0/aframe.min.js"></script>
  <script src="/aframe-stereo-component.min.js"></script>
</svelte:head>

<a-scene>
  <a-assets>
    <!-- svelte-ignore a11y-missing-attribute -->
    <img id="left" src="/left.jpg">
    <!-- svelte-ignore a11y-missing-attribute -->
    <img id="right" src="/right.jpg">

    <audio id="recording" src="/audio.mp4" preload="auto"></audio>
  </a-assets>

  <a-sky id="sky1" src="#left" stereo="eye:left"></a-sky>
  <a-sky id="sky2" src="#right" stereo="eye:right"></a-sky>

  <a-entity id="ambient" geometry="primitive: plane" material="color: blue"
          position="0 0 0" sound="src: #recording; autoplay: true; loop: true"></a-entity>
</a-scene>
