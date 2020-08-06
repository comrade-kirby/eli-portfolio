<script>
  export let slide

  let xStart

  const touchStart = (event) => xStart = event.touches[0].clientX

  const touchMove = (event) => {
    if (!xStart) { return }

    const xCurrent = event.touches[0].clientX
    const xDiff = xStart - xCurrent
    
    xDiff > 0 ? slide('next') : slide('previous')
    
    xStart = null
  }
</script>

<div 
  class='swipe-detect'
  on:touchstart={touchStart}
  on:touchmove={touchMove}
  >
</div>

<style>
  .swipe-detect {
    min-width:  100%;
    min-height: 100%;
    position: absolute;
  }
</style>