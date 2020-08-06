<script>
  export let slide

  let xStart, yStart

  const touchStart = (event) => {
    xStart = event.touches[0].clientX
    yStart = event.touches[0].clientY
  }
  
  const touchMove = (event) => {
    if (!xStart || !yStart) { return }

    const xCurrent = event.touches[0].clientX
    const yCurrent = event.touches[0].clientY
  
    const xDiff = xStart - xCurrent
    const yDiff = yStart - yCurrent
    
    if ( Math.abs( xDiff ) > Math.abs( yDiff ) ) {
      xDiff > 0 ? slide('next') : slide('previous')
    }

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
    display: flex;
    min-width:  100%;
    min-height: 100%;
    position: absolute;
    padding: 0 50px;
    margin-bottom: 150px;
    align-self: center;
  }
</style>