# hex-fog-of-war

const draw = SVG().addTo('#hex').size('100%', '100%')

const Hex = Honeycomb.extendHex({ size: 30 })
const Grid = Honeycomb.defineGrid(Hex)
// get the corners of a hex (they're the same for all hexes created with the same Hex factory)
const corners = Hex().corners()
// an SVG symbol can be reused
const hexSymbol = draw.symbol()
    // map the corners' positions to a string and create a polygon
    .polygon(corners.map(({ x, y }) => `${x},${y}`))
    .fill('none')
    .stroke({ width: 1, color: '#999' })

// render 10,000 hexes
Grid.rectangle({ width: 100, height: 100 }).forEach(hex => {
    const { x, y } = hex.toPoint()
    // use hexSymbol and set its position for each hex
    draw.use(hexSymbol).translate(x, y)
})



<div id="wrapper" class="full">
<img class="full" id="map" src="https://www.freeworldmaps.net/europe/france/france-physical-map.jpg" alt="alternatetext">
<div class="full" id="hex" >
</div>
</div>


html,
body, .full {
  height: 100%;
  width: 100%;
}

#hex {
  z-index: 20;
  position: absolute;
  top: 0;
}


![image](https://user-images.githubusercontent.com/31974070/162892745-18885079-2219-479f-9968-afd156c9c1b7.png)
