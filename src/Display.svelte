<script>
  import Shadow from "./Shadow.svelte";

  let speed = 18;
  let progress = 1;

  setInterval(() => {
    speed += Math.round(Math.random() * 2 - 1);
    if (speed < 10) {
      speed += 1;
    }
    progress += 1;
  }, 500);
</script>

<style>
  section {
    display: flex;
    align-items: center;
    flex-direction: column;
    width: 100vw;
    height: 100vh;
    overflow: hidden;
  }
  .box {
    margin-top: 100px;
    width: 350px;
    color: rgba(110, 110, 110, 0.5);
    /* color: green; */
    position: relative;
  }
  .box :global(.shadow-left) {
    top: -33%;
    right: 29%;
    transform: translate(0, -50%) rotate(45deg);
  }
  .box :global(.shadow-leftback) {
    top: 60%;
    right: 100%;
    transform: translate(0, -50%);
  }
  .box :global(.shadow-right) {
    top: 80%;
    left: 100%;
    transform: translate(0, -50%) scale(-1, 1);
  }
</style>

<section>
  <h2>Sensor Data</h2>
  <div class="box">
    <svg viewBox="0 0 14 20" width="100%"><style>
        .speed {
          font: italic 3px sans-serif;
          fill: #88b1ff;
        }
      </style>
      <path d="M0,9 L9,0 L14,0 L14,20 L0,20z" fill="#444" />
      <text x="1.5" y="14" class="speed">{speed} km/h</text>
    </svg>
    <Shadow
      class="shadow-left"
      red={progress % 11 === 0}
      distance="∞"
      distanceMin={75}
      distanceMax={220} />
    <Shadow
      class="shadow-leftback"
      green={progress % 3 === 0}
      yellow={progress % 4 === 0}
      distance="∞"
      distanceMin={56}
      distanceMax={198} />
    <Shadow
      class="shadow-right"
      green={progress % 3 === 0}
      distance="∞"
      distanceMin={34}
      distanceMax={121}
      mirror />
  </div>
</section>
