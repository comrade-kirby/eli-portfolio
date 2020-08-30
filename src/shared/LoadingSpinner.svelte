<script>
  import { fade } from 'svelte/transition'

</script>

<svg 
  transition:fade
  xmlns="http://www.w3.org/2000/svg" 
  xmlns:xlink="http://www.w3.org/1999/xlink" 
  viewBox="0 0 380 380">
  <path d="M225.51 175.37c9.67 5.44 14.5 10.33 14.49 14.67-.01 4.34-4.83 9.23-14.46 14.66 3.44 10.27 3.38 17.17-.18 20.73-3.56 3.56-10.43 3.58-20.61.08-4.59 9.73-9.49 14.61-14.71 14.61-5.22 0-10.07-4.84-14.54-14.53-10.93 2.89-17.9 2.83-20.93-.19-3.02-3.02-3.01-9.9.04-20.66-9.77-4.4-14.65-9.31-14.65-14.74-.01-5.42 4.89-10.31 14.69-14.67-3.36-10.4-3.36-17.27 0-20.64 3.36-3.36 10.25-3.38 20.67-.08 5.25-9.74 10.16-14.62 14.72-14.61 4.56.01 9.43 4.91 14.63 14.7 9.93-3.91 16.84-3.92 20.73-.02 3.9 3.9 3.93 10.8.11 20.69z" id="a"/>
</svg>

<style>
  svg {
    z-index: 1;
    animation: rotate 6s 1.33s infinite;
  }

  path {
    stroke: black;
    fill: none;
    stroke-dasharray: 346;
    animation: draw 2s infinite;
  }

  @keyframes draw {
    0% {
      stroke-dashoffset: 692;
    }
    
    33% {
      stroke-dashoffset: 346;
    }

    67% {
      stroke-dashoffset: 0;
    }
    
    100% {
      stroke-dashoffset: 0;
    }
  }
  
  @keyframes rotate {
    0% {
      transform: rotate(0deg)
    }

    11.1% {
      transform: rotate(120deg)
    }

    22.2% {
      transform: rotate(120deg)
    }

    33.3% {
      transform: rotate(120deg)
    }

    44.4% {
      transform: rotate(240deg)
    }

    55.6% {
      transform: rotate(240deg)
    }

    66.7% {
      transform: rotate(240deg)
    }

    77.6% {
      transform: rotate(360deg)
    }

    88.9% {
      transform: rotate(360deg)
    }
    
    100% {
      transform: rotate(360deg)
    }
  }
</style>