<script>
  let {
    size = "64px",
    strokeWidth = "6px",
    ariaLabel = "Loading",
    color = "black",
  } = $props();
</script>

<div
  aria-label={ariaLabel}
  class="loading-indicator"
  style={`height: ${size}; width: ${size}; --loader-color: ${color};`}
>
  {#each [...new Array(4)] as index}
    <div
      key={index}
      style={`border-width: ${strokeWidth}; height: ${size}; width: ${size}`}
      class="circle"
    ></div>
  {/each}
</div>

<style>
  .loading-indicator {
    bottom: 0;
    left: 0;
    margin: auto;
    position: absolute;
    right: 0;
    top: 0;
    z-index: 2;
  }

  .loading-indicator:nth-child(1) {
    animation-delay: -0.45s;
  }

  .loading-indicator:nth-child(2) {
    animation-delay: -0.3s;
  }

  .loading-indicator:nth-child(3) {
    animation-delay: -0.15s;
  }

  @keyframes fullRotate {
    0% {
      transform: rotate(0deg);
    }

    100% {
      transform: rotate(360deg);
    }
  }

  .circle {
    --loader-color-20: color-mix(in srgb, var(--loader-color), transparent 80%);
    animation: fullRotate 1.5s cubic-bezier(0.5, 0, 0.5, 1) infinite;
    border-color: var(--loader-color) var(--loader-color-20)
      var(--loader-color-20) var(--loader-color-20);
    border-radius: 50%;
    border-style: solid;
    box-sizing: border-box;
    display: block;
    position: absolute;
  }
</style>
