<script>
  export let green = false;
  export let yellow = false;
  export let red = false;
  export let mirror = false;
  let transform = "";
  if (mirror) {
    transform = "scale(-1, 1) translate(-12, 0)";
  }
</script>

<style>
  svg {
    position: absolute;
  }
  .green {
    color: green;
  }
  .yellow {
    color: yellow;
  }
  .red {
    color: red;
  }
</style>

<svg
  class={$$props.class}
  class:green
  class:yellow
  class:red
  viewBox="0 0 20 20"
  width="200%"><style>
    .distance {
      font: italic 0.7px sans-serif;
      fill: #fbdfaa;
    }
  </style>
  <path d="M20,9 L20,11 L0,20 L0,0z" fill="currentColor" />
  <!-- <text x="14" y="9" class="distance" {transform} transform-origin="center">
    {$$props.distance}
    cm
  </text> -->
  <text x="14" y="10" class="distance" {transform} transform-origin="center">
    min
    {$$props.distanceMin}
    cm
  </text>
  <text x="14" y="11" class="distance" {transform} transform-origin="center">
    max
    {$$props.distanceMax}
    cm
  </text>
</svg>
