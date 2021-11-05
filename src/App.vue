<template>
  <div
    id="app"
    :class="{ 'has-mouse': hasMouse }"
    @touchstart="hasMouse = false"
  >
    <header>
      <h1>
        <a href="https://www.vulica-brasil.by/" title="Vulica Brasil website" target="_blank">
          <img src="@/assets/logo-vb.png"/>
        </a>
      </h1>
    </header>
    <section>
      <div id="container">
        <Flipbook
          class="flipbook"
          :pages="pages"
          :pagesHiRes="pagesHiRes"
          :startPage="pageNum"
          :gloss="0.2"
          :ambient="0.2"
          :zooms="[1, 2]"
          v-slot="flipbook"
          ref="flipbook"
          @flip-left-start="onFlipLeftStart"
          @flip-left-end="onFlipLeftEnd"
          @flip-right-start="onFlipRightStart"
          @flip-right-end="onFlipRightEnd"
          @zoom-start="onZoomStart"
          @zoom-end="onZoomEnd"
        >
          <div class="button left"> &lt; </div>
          <div class="action-bar">
            <span class="page-num">
              PAGE {{ flipbook.page }} OF {{ flipbook.numPages }}
            </span>
          </div>
          <div class="button right"> &gt; </div>
        </Flipbook>
      </div>
    </section>
    <footer>
      <a href="https://www.instagram.com/vulicabrasil.galeria/" title="Instagram" target="_blank">GALLERY</a>
      <a href="https://www.youtube.com/channel/UCkFtwnKHUWkJZtudfdHDutQ/featured" title="YouTube" target="_blank">YOUTUBE</a>
      <a href="https://www.facebook.com/vulicabrasil" title="Facebook" target="_blank">FACEBOOK</a>
      <a href="https://www.vulica-brasil.by/" title="Website" target="_blank">WEB</a>
      <a href="https://vimeo.com/vulicabrasil" title="Vimeo" target="_blank">VIMEO</a>
      <a href="https://www.mixcloud.com/VulicaBrasil/" title="Mixcloud" target="_blank">MIXCLOUD</a>
      <a href="https://www.linkedin.com/company/vulicabrasil" title="LinkedIn" target="_blank">LINKEDIN</a>
    </footer>
  </div>
</template>

<script lang="coffee">
import 'vue-material-design-icons/styles.css'
import Ribbon from 'vue-ribbon'
import LeftIcon from 'vue-material-design-icons/ChevronLeftCircle'
import RightIcon from 'vue-material-design-icons/ChevronRightCircle'
import PlusIcon from 'vue-material-design-icons/PlusCircle'
import MinusIcon from 'vue-material-design-icons/MinusCircle'
import Flipbook from './Flipbook'

export default
  name: 'app'
  components: { Flipbook, LeftIcon, RightIcon, PlusIcon, MinusIcon, Ribbon }
  data: ->
    pages: [],
    pagesHiRes: [],
    hasMouse: true
    pageNum: null
  methods:
    onFlipLeftStart: (page) -> console.log 'flip-left-start', page
    onFlipLeftEnd: (page) ->
      console.log 'flip-left-end', page
      window.location.hash = '#' + page
    onFlipRightStart: (page) -> console.log 'flip-right-start', page
    onFlipRightEnd: (page) ->
      console.log 'flip-right-end', page
      window.location.hash = '#' + page
    onZoomStart: (zoom) -> console.log 'zoom-start', zoom
    onZoomEnd: (zoom) -> console.log 'zoom-end', zoom
    setPageFromHash: ->
      n = parseInt window.location.hash.slice(1), 10
      @pageNum = n if isFinite n
  mounted: ->
    window.addEventListener 'keydown', (ev) =>
      flipbook = @$refs.flipbook
      return unless flipbook
      flipbook.flipLeft() if ev.keyCode == 37 and flipbook.canFlipLeft
      flipbook.flipRight() if ev.keyCode == 39 and flipbook.canFlipRight

    setTimeout (=>
      @pages = [
        null,
        "assets/0001_1600px.jpg",
        "assets/0002_1600px.jpg",
        "assets/0003_1600px.jpg",
        "assets/0004_1600px.jpg",
        "assets/0005_1600px.jpg",
        "assets/0006_1600px.jpg",
        "assets/0007_1600px.jpg",
        "assets/0008_1600px.jpg",
        "assets/0009_1600px.jpg",
        "assets/0010_1600px.jpg",
        "assets/0011_1600px.jpg",
        "assets/0012_1600px.jpg",
        "assets/0013_1600px.jpg",
        "assets/0014_1600px.jpg",
        "assets/0015_1600px.jpg",
        "assets/0016_1600px.jpg",
        "assets/0017_1600px.jpg",
        "assets/0018_1600px.jpg",
        "assets/0019_1600px.jpg",
        "assets/0020_1600px.jpg",
        "assets/0021_1600px.jpg",
        "assets/0022_1600px.jpg",
        "assets/0023_1600px.jpg",
        "assets/0024_1600px.jpg",
        "assets/0025_1600px.jpg",
        "assets/0026_1600px.jpg",
        "assets/0027_1600px.jpg",
        "assets/0028_1600px.jpg",
        "assets/0029_1600px.jpg",
        "assets/0030_1600px.jpg",
        "assets/0031_1600px.jpg",
        "assets/0032_1600px.jpg",
        "assets/0033_1600px.jpg",
        "assets/0034_1600px.jpg",
        "assets/0035_1600px.jpg",
        "assets/0036_1600px.jpg",
        "assets/0037_1600px.jpg",
        "assets/0038_1600px.jpg",
        "assets/0039_1600px.jpg",
        "assets/0040_1600px.jpg",
        "assets/0041_1600px.jpg",
        "assets/0042_1600px.jpg",
        "assets/0043_1600px.jpg",
        "assets/0044_1600px.jpg",
        "assets/0045_1600px.jpg",
        "assets/0046_1600px.jpg",
        "assets/0047_1600px.jpg",
        "assets/0048_1600px.jpg",
        "assets/0049_1600px.jpg",
        "assets/0050_1600px.jpg",
        "assets/0051_1600px.jpg",
        "assets/0052_1600px.jpg",
        "assets/0053_1600px.jpg",
        "assets/0054_1600px.jpg",
        "assets/0055_1600px.jpg",
        "assets/0056_1600px.jpg",
        "assets/0057_1600px.jpg",
        "assets/0058_1600px.jpg",
        "assets/0059_1600px.jpg",
        "assets/0060_1600px.jpg",
        "assets/0061_1600px.jpg",
        "assets/0062_1600px.jpg",
        "assets/0063_1600px.jpg",
        "assets/0064_1600px.jpg",
        "assets/0065_1600px.jpg",
        "assets/0066_1600px.jpg",
        "assets/0067_1600px.jpg",
        "assets/0068_1600px.jpg",
        "assets/0069_1600px.jpg",
        "assets/0070_1600px.jpg",
        "assets/0071_1600px.jpg",
        "assets/0072_1600px.jpg",
        "assets/0073_1600px.jpg",
        "assets/0074_1600px.jpg",
        "assets/0075_1600px.jpg",
        "assets/0076_1600px.jpg",
        "assets/0077_1600px.jpg",
        "assets/0078_1600px.jpg",
        "assets/0079_1600px.jpg",
        "assets/0080_1600px.jpg",
        "assets/0081_1600px.jpg",
        "assets/0082_1600px.jpg",
        "assets/0083_1600px.jpg",
        "assets/0084_1600px.jpg",
        "assets/0085_1600px.jpg",
        "assets/0086_1600px.jpg",
        "assets/0087_1600px.jpg",
        "assets/0088_1600px.jpg",
        "assets/0089_1600px.jpg",
        "assets/0090_1600px.jpg",
        "assets/0091_1600px.jpg",
        "assets/0092_1600px.jpg",
        "assets/0093_1600px.jpg",
        "assets/0094_1600px.jpg",
        "assets/0095_1600px.jpg",
        "assets/0096_1600px.jpg",
        "assets/0097_1600px.jpg",
        "assets/0098_1600px.jpg",
        "assets/0099_1600px.jpg",
        "assets/0100_1600px.jpg",
        "assets/0101_1600px.jpg",
        "assets/0102_1600px.jpg",
        "assets/0103_1600px.jpg",
        "assets/0104_1600px.jpg",
        "assets/0105_1600px.jpg",
        "assets/0106_1600px.jpg",
        "assets/0107_1600px.jpg",
        "assets/0108_1600px.jpg",
        "assets/0109_1600px.jpg",
        "assets/0110_1600px.jpg",
        "assets/0111_1600px.jpg",
        "assets/0112_1600px.jpg",
        "assets/0113_1600px.jpg",
        "assets/0114_1600px.jpg",
        "assets/0115_1600px.jpg",
        "assets/0116_1600px.jpg",
        "assets/0117_1600px.jpg",
        "assets/0118_1600px.jpg",
        "assets/0119_1600px.jpg",
        "assets/0120_1600px.jpg",
        "assets/0121_1600px.jpg",
        "assets/0122_1600px.jpg",
        "assets/0123_1600px.jpg",
        "assets/0124_1600px.jpg",
        "assets/0125_1600px.jpg",
        "assets/0126_1600px.jpg",
        "assets/0127_1600px.jpg",
        "assets/0128_1600px.jpg",
        "assets/0129_1600px.jpg",
        "assets/0130_1600px.jpg",
        "assets/0131_1600px.jpg",
        "assets/0132_1600px.jpg",
        "assets/0133_1600px.jpg",
        "assets/0134_1600px.jpg",
        "assets/0135_1600px.jpg",
        "assets/0136_1600px.jpg",
        "assets/0137_1600px.jpg",
        "assets/0138_1600px.jpg",
        "assets/0139_1600px.jpg",
        "assets/0140_1600px.jpg",
        "assets/0141_1600px.jpg",
        "assets/0142_1600px.jpg",
        "assets/0143_1600px.jpg",
        "assets/0144_1600px.jpg",
        "assets/0145_1600px.jpg",
        "assets/0146_1600px.jpg",
        "assets/0147_1600px.jpg",
        "assets/0148_1600px.jpg",
        "assets/0149_1600px.jpg",
        "assets/0150_1600px.jpg",
        "assets/0151_1600px.jpg",
        "assets/0152_1600px.jpg",
        "assets/0153_1600px.jpg",
        "assets/0154_1600px.jpg",
        "assets/0155_1600px.jpg",
        "assets/0156_1600px.jpg",
        "assets/0157_1600px.jpg",
        "assets/0158_1600px.jpg",
        "assets/0159_1600px.jpg",
        "assets/0160_1600px.jpg",
        "assets/0161_1600px.jpg",
        "assets/0162_1600px.jpg",
        "assets/0163_1600px.jpg",
        "assets/0164_1600px.jpg",
        "assets/0165_1600px.jpg",
        "assets/0166_1600px.jpg",
        "assets/0167_1600px.jpg",
        "assets/0168_1600px.jpg",
        "assets/0169_1600px.jpg",
        "assets/0170_1600px.jpg",
        "assets/0171_1600px.jpg",
        "assets/0172_1600px.jpg",
        "assets/0173_1600px.jpg",
        "assets/0174_1600px.jpg",
        "assets/0175_1600px.jpg",
        "assets/0176_1600px.jpg",
        "assets/0177_1600px.jpg",
        "assets/0178_1600px.jpg",
        "assets/0179_1600px.jpg",
        "assets/0180_1600px.jpg",
        "assets/0181_1600px.jpg",
        "assets/0182_1600px.jpg",
        "assets/0183_1600px.jpg",
        "assets/0184_1600px.jpg",
        "assets/0185_1600px.jpg",
        "assets/0186_1600px.jpg",
        "assets/0187_1600px.jpg",
        "assets/0188_1600px.jpg",
        "assets/0189_1600px.jpg",
        "assets/0190_1600px.jpg",
        "assets/0191_1600px.jpg",
        "assets/0192_1600px.jpg",
        "assets/0193_1600px.jpg",
        "assets/0194_1600px.jpg",
        "assets/0195_1600px.jpg",
        "assets/0196_1600px.jpg",
        "assets/0197_1600px.jpg",
        "assets/0198_1600px.jpg",
        "assets/0199_1600px.jpg",
        "assets/0200_1600px.jpg",
        "assets/0201_1600px.jpg",
        "assets/0202_1600px.jpg",
        "assets/0203_1600px.jpg",
        "assets/0204_1600px.jpg",
        "assets/0205_1600px.jpg",
        "assets/0206_1600px.jpg",
        "assets/0207_1600px.jpg",
        "assets/0208_1600px.jpg",
        "assets/0209_1600px.jpg",
        "assets/0210_1600px.jpg",
        "assets/0211_1600px.jpg",
        "assets/0212_1600px.jpg",
        "assets/0213_1600px.jpg",
        "assets/0214_1600px.jpg",
        "assets/0215_1600px.jpg",
        "assets/0216_1600px.jpg",
        "assets/0217_1600px.jpg",
        "assets/0218_1600px.jpg",
        "assets/0219_1600px.jpg",
        "assets/0220_1600px.jpg",
        "assets/0221_1600px.jpg",
        "assets/0222_1600px.jpg",
        "assets/0223_1600px.jpg",
        "assets/0224_1600px.jpg",
        "assets/0225_1600px.jpg",
        "assets/0226_1600px.jpg"
      ]
      
      @pagesHiRes = [
        null,
        "raw-assets/0001.jpg",
        "raw-assets/0002.jpg",
        "raw-assets/0003.jpg",
        "raw-assets/0004.jpg",
        "raw-assets/0005.jpg",
        "raw-assets/0006.jpg",
        "raw-assets/0007.jpg",
        "raw-assets/0008.jpg",
        "raw-assets/0009.jpg",
        "raw-assets/0010.jpg",
        "raw-assets/0011.jpg",
        "raw-assets/0012.jpg",
        "raw-assets/0013.jpg",
        "raw-assets/0014.jpg",
        "raw-assets/0015.jpg",
        "raw-assets/0016.jpg",
        "raw-assets/0017.jpg",
        "raw-assets/0018.jpg",
        "raw-assets/0019.jpg",
        "raw-assets/0020.jpg",
        "raw-assets/0021.jpg",
        "raw-assets/0022.jpg",
        "raw-assets/0023.jpg",
        "raw-assets/0024.jpg",
        "raw-assets/0025.jpg",
        "raw-assets/0026.jpg",
        "raw-assets/0027.jpg",
        "raw-assets/0028.jpg",
        "raw-assets/0029.jpg",
        "raw-assets/0030.jpg",
        "raw-assets/0031.jpg",
        "raw-assets/0032.jpg",
        "raw-assets/0033.jpg",
        "raw-assets/0034.jpg",
        "raw-assets/0035.jpg",
        "raw-assets/0036.jpg",
        "raw-assets/0037.jpg",
        "raw-assets/0038.jpg",
        "raw-assets/0039.jpg",
        "raw-assets/0040.jpg",
        "raw-assets/0041.jpg",
        "raw-assets/0042.jpg",
        "raw-assets/0043.jpg",
        "raw-assets/0044.jpg",
        "raw-assets/0045.jpg",
        "raw-assets/0046.jpg",
        "raw-assets/0047.jpg",
        "raw-assets/0048.jpg",
        "raw-assets/0049.jpg",
        "raw-assets/0050.jpg",
        "raw-assets/0051.jpg",
        "raw-assets/0052.jpg",
        "raw-assets/0053.jpg",
        "raw-assets/0054.jpg",
        "raw-assets/0055.jpg",
        "raw-assets/0056.jpg",
        "raw-assets/0057.jpg",
        "raw-assets/0058.jpg",
        "raw-assets/0059.jpg",
        "raw-assets/0060.jpg",
        "raw-assets/0061.jpg",
        "raw-assets/0062.jpg",
        "raw-assets/0063.jpg",
        "raw-assets/0064.jpg",
        "raw-assets/0065.jpg",
        "raw-assets/0066.jpg",
        "raw-assets/0067.jpg",
        "raw-assets/0068.jpg",
        "raw-assets/0069.jpg",
        "raw-assets/0070.jpg",
        "raw-assets/0071.jpg",
        "raw-assets/0072.jpg",
        "raw-assets/0073.jpg",
        "raw-assets/0074.jpg",
        "raw-assets/0075.jpg",
        "raw-assets/0076.jpg",
        "raw-assets/0077.jpg",
        "raw-assets/0078.jpg",
        "raw-assets/0079.jpg",
        "raw-assets/0080.jpg",
        "raw-assets/0081.jpg",
        "raw-assets/0082.jpg",
        "raw-assets/0083.jpg",
        "raw-assets/0084.jpg",
        "raw-assets/0085.jpg",
        "raw-assets/0086.jpg",
        "raw-assets/0087.jpg",
        "raw-assets/0088.jpg",
        "raw-assets/0089.jpg",
        "raw-assets/0090.jpg",
        "raw-assets/0091.jpg",
        "raw-assets/0092.jpg",
        "raw-assets/0093.jpg",
        "raw-assets/0094.jpg",
        "raw-assets/0095.jpg",
        "raw-assets/0096.jpg",
        "raw-assets/0097.jpg",
        "raw-assets/0098.jpg",
        "raw-assets/0099.jpg",
        "raw-assets/0100.jpg",
        "raw-assets/0101.jpg",
        "raw-assets/0102.jpg",
        "raw-assets/0103.jpg",
        "raw-assets/0104.jpg",
        "raw-assets/0105.jpg",
        "raw-assets/0106.jpg",
        "raw-assets/0107.jpg",
        "raw-assets/0108.jpg",
        "raw-assets/0109.jpg",
        "raw-assets/0110.jpg",
        "raw-assets/0111.jpg",
        "raw-assets/0112.jpg",
        "raw-assets/0113.jpg",
        "raw-assets/0114.jpg",
        "raw-assets/0115.jpg",
        "raw-assets/0116.jpg",
        "raw-assets/0117.jpg",
        "raw-assets/0118.jpg",
        "raw-assets/0119.jpg",
        "raw-assets/0120.jpg",
        "raw-assets/0121.jpg",
        "raw-assets/0122.jpg",
        "raw-assets/0123.jpg",
        "raw-assets/0124.jpg",
        "raw-assets/0125.jpg",
        "raw-assets/0126.jpg",
        "raw-assets/0127.jpg",
        "raw-assets/0128.jpg",
        "raw-assets/0129.jpg",
        "raw-assets/0130.jpg",
        "raw-assets/0131.jpg",
        "raw-assets/0132.jpg",
        "raw-assets/0133.jpg",
        "raw-assets/0134.jpg",
        "raw-assets/0135.jpg",
        "raw-assets/0136.jpg",
        "raw-assets/0137.jpg",
        "raw-assets/0138.jpg",
        "raw-assets/0139.jpg",
        "raw-assets/0140.jpg",
        "raw-assets/0141.jpg",
        "raw-assets/0142.jpg",
        "raw-assets/0143.jpg",
        "raw-assets/0144.jpg",
        "raw-assets/0145.jpg",
        "raw-assets/0146.jpg",
        "raw-assets/0147.jpg",
        "raw-assets/0148.jpg",
        "raw-assets/0149.jpg",
        "raw-assets/0150.jpg",
        "raw-assets/0151.jpg",
        "raw-assets/0152.jpg",
        "raw-assets/0153.jpg",
        "raw-assets/0154.jpg",
        "raw-assets/0155.jpg",
        "raw-assets/0156.jpg",
        "raw-assets/0157.jpg",
        "raw-assets/0158.jpg",
        "raw-assets/0159.jpg",
        "raw-assets/0160.jpg",
        "raw-assets/0161.jpg",
        "raw-assets/0162.jpg",
        "raw-assets/0163.jpg",
        "raw-assets/0164.jpg",
        "raw-assets/0165.jpg",
        "raw-assets/0166.jpg",
        "raw-assets/0167.jpg",
        "raw-assets/0168.jpg",
        "raw-assets/0169.jpg",
        "raw-assets/0170.jpg",
        "raw-assets/0171.jpg",
        "raw-assets/0172.jpg",
        "raw-assets/0173.jpg",
        "raw-assets/0174.jpg",
        "raw-assets/0175.jpg",
        "raw-assets/0176.jpg",
        "raw-assets/0177.jpg",
        "raw-assets/0178.jpg",
        "raw-assets/0179.jpg",
        "raw-assets/0180.jpg",
        "raw-assets/0181.jpg",
        "raw-assets/0182.jpg",
        "raw-assets/0183.jpg",
        "raw-assets/0184.jpg",
        "raw-assets/0185.jpg",
        "raw-assets/0186.jpg",
        "raw-assets/0187.jpg",
        "raw-assets/0188.jpg",
        "raw-assets/0189.jpg",
        "raw-assets/0190.jpg",
        "raw-assets/0191.jpg",
        "raw-assets/0192.jpg",
        "raw-assets/0193.jpg",
        "raw-assets/0194.jpg",
        "raw-assets/0195.jpg",
        "raw-assets/0196.jpg",
        "raw-assets/0197.jpg",
        "raw-assets/0198.jpg",
        "raw-assets/0199.jpg",
        "raw-assets/0200.jpg",
        "raw-assets/0201.jpg",
        "raw-assets/0202.jpg",
        "raw-assets/0203.jpg",
        "raw-assets/0204.jpg",
        "raw-assets/0205.jpg",
        "raw-assets/0206.jpg",
        "raw-assets/0207.jpg",
        "raw-assets/0208.jpg",
        "raw-assets/0209.jpg",
        "raw-assets/0210.jpg",
        "raw-assets/0211.jpg",
        "raw-assets/0212.jpg",
        "raw-assets/0213.jpg",
        "raw-assets/0214.jpg",
        "raw-assets/0215.jpg",
        "raw-assets/0216.jpg",
        "raw-assets/0217.jpg",
        "raw-assets/0218.jpg",
        "raw-assets/0219.jpg",
        "raw-assets/0220.jpg",
        "raw-assets/0221.jpg",
        "raw-assets/0222.jpg",
        "raw-assets/0223.jpg",
        "raw-assets/0224.jpg",
        "raw-assets/0225.jpg",
        "raw-assets/0226.jpg"
    ]
    ), 1

    window.addEventListener 'hashchange', @setPageFromHash
    @setPageFromHash()
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
}

@font-face {
  font-family: "Base&Bloom Base&Bloom";
  src: url(fonts/Base&Bloom-Base&Bloom-Trial.ttf) format("truetype");
}

body {
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-content: stretch;
  align-items: center;

  width: 100%;

  overflow-x: hidden;
  overflow-y: hidden;
  background-color: #ffffff;

  font-family: "Base&Bloom Base&Bloom", sans-serif;
}

header {
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: center;
  align-content: center;
  align-items: center;

  height: 100px;
  width: 100%;

  z-index: 10;
  position: absolute;
  top: 0;

  background: linear-gradient(#ffffff, rgba(255, 255, 255, 0));;
}

header h1 a {
  text-decoration: none;
}

header h1 a:active {
  text-decoration: none;
  color: #000000;
}

header h1 a:visited {
  text-decoration: none;
  color: #000000;
}

header h1 a img {
  height: 1.5em;
  width: auto;
}

section {
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: center;
  align-content: center;
  align-items: center;

  height: calc(100vh - 200px);
  width: 100%;

  margin-top: 120px;

  padding-bottom: 20px;

  background-color: #ffffff;
}

footer {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-around;
  align-content: center;
  align-items: center;

  height: 60px;
  width: 100%;

  background-color: #34d331;
}

footer a {
  width: 80px;
  text-align: center;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: auto;
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
}

a {
  color: inherit;
}

.action-bar {
  width: 100%;
  height: 30px;
  padding-top: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.action-bar .page-num {
  user-select: none;
  font-size: 11px;
  margin: 0 10px;
}

.flipbook {
  display: flex;
  flex-direction: column-reverse;
  flex-wrap: nowrap;
  justify-content: flex-end;
  align-content: center;
  align-items: center;
}

.flipbook .button {
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: center;
  align-content: center;
  align-items: center;

  font-size: 4em;

  position: absolute;
  top: calc(50% - 32px);

  width: 64px;
  height: 64px;
}

.flipbook .button.left {
  left: 3em;
}

.flipbook .button.right {
  right: 3em;
}

.flipbook .viewport {
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-content: center;
  align-items: center;

  width: 90vw;
  height: calc(100vh - 250px);
}

.flipbook .bounding-box {
  box-shadow: 0 0 20px #000;
}

@media only screen and (max-device-width: 600px) {
  html, body {
    overflow-y: visible;
  }

  section {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: flex-start;
    align-content: flex-start;
    align-items: center;

    height: 100vh;
    width: 100%;

    margin: 0;
    padding: 0;

    background-color: #ffffff;
  }

  footer {
    flex-direction: column;
    height: 240px;
    padding: 20px 0;
  }

  .flipbook {
    margin-top: 100px;
  }

  .flipbook .button {
    display: none;
  }

  .flipbook .action-bar {
    padding: 0;
  }

  .flipbook .bounding-box {
    height: calc(90vw * 1.18) !important;
  }

  .flipbook .viewport {
    width: 90vw;
  }

  .left, .right {
    display: none;
  }
}

@media only screen and (min-device-width: 200px) 
                   and (max-device-width: 960px) 
                   and (orientation: landscape) {
  header, footer {
    display: none;
  }

  section {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: flex-start;
    align-content: flex-start;
    align-items: center;

    height: 100vh;
    width: 100%;

    margin: 0;
    padding: 0;

    background-color: #ffffff;
  }

  .flipbook .button {
    display: none;
  }

  .flipbook .action-bar {
    position: absolute;
    z-index: 10;
    bottom: 0;
  }

  .flipbook .action-bar .page-num {
    padding: 5px;
    background-color: #ffffff4f;
    border-radius: 2px;
  }

  .flipbook .bounding-box {
    height: 100vh !important;
  }

  .flipbook .viewport {
    width: 100vw;
    height: 100vh !important;
  }

  .left, .right {
    display: none;
  }
}
</style>
