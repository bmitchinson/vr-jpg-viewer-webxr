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
  </a-assets>

  <a-entity camera look-controls position="0 0 0" stereocam="eye:left;"></a-entity>

  <a-sky id="sky1" src="#left" stereo="eye:left"></a-sky>
  <a-sky id="sky2" src="#right" stereo="eye:right"></a-sky>
</a-scene>
