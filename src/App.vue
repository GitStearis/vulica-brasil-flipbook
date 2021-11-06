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
        "compressed/1.jpg",
        "compressed/2.jpg",
        "compressed/3.jpg",
        "compressed/4.jpg",
        "compressed/5.jpg",
        "compressed/6.jpg",
        "compressed/7.jpg",
        "compressed/8.jpg",
        "compressed/9.jpg",
        "compressed/10.jpg",
        "compressed/11.jpg",
        "compressed/12.jpg",
        "compressed/13.jpg",
        "compressed/14.jpg",
        "compressed/15.jpg",
        "compressed/16.jpg",
        "compressed/17.jpg",
        "compressed/18.jpg",
        "compressed/19.jpg",
        "compressed/20.jpg",
        "compressed/21.jpg",
        "compressed/22.jpg",
        "compressed/23.jpg",
        "compressed/24.jpg",
        "compressed/25.jpg",
        "compressed/26.jpg",
        "compressed/27.jpg",
        "compressed/28.jpg",
        "compressed/29.jpg",
        "compressed/30.jpg",
        "compressed/31.jpg",
        "compressed/32.jpg",
        "compressed/33.jpg",
        "compressed/34.jpg",
        "compressed/35.jpg",
        "compressed/36.jpg",
        "compressed/37.jpg",
        "compressed/38.jpg",
        "compressed/39.jpg",
        "compressed/40.jpg",
        "compressed/41.jpg",
        "compressed/42.jpg",
        "compressed/43.jpg",
        "compressed/44.jpg",
        "compressed/45.jpg",
        "compressed/46.jpg",
        "compressed/47.jpg",
        "compressed/48.jpg",
        "compressed/49.jpg"
      ]
      
      @pagesHiRes = [
        null,
        "original/1.jpg",
        "original/2.jpg",
        "original/3.jpg",
        "original/4.jpg",
        "original/5.jpg",
        "original/6.jpg",
        "original/7.jpg",
        "original/8.jpg",
        "original/9.jpg",
        "original/10.jpg",
        "original/11.jpg",
        "original/12.jpg",
        "original/13.jpg",
        "original/14.jpg",
        "original/15.jpg",
        "original/16.jpg",
        "original/17.jpg",
        "original/18.jpg",
        "original/19.jpg",
        "original/20.jpg",
        "original/21.jpg",
        "original/22.jpg",
        "original/23.jpg",
        "original/24.jpg",
        "original/25.jpg",
        "original/26.jpg",
        "original/27.jpg",
        "original/28.jpg",
        "original/29.jpg",
        "original/30.jpg",
        "original/31.jpg",
        "original/32.jpg",
        "original/33.jpg",
        "original/34.jpg",
        "original/35.jpg",
        "original/36.jpg",
        "original/37.jpg",
        "original/38.jpg",
        "original/39.jpg",
        "original/40.jpg",
        "original/41.jpg",
        "original/42.jpg",
        "original/43.jpg",
        "original/44.jpg",
        "original/45.jpg",
        "original/46.jpg",
        "original/47.jpg",
        "original/48.jpg",
        "original/49.jpg"
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
    padding-top: 18px;
  }

  .flipbook .bounding-box {
    height: calc(90vw * 1.18) !important;
  }

  .flipbook .viewport {
    height: calc(90vw * 1.18) !important;
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

  .flipbook {
    position: relative;
  }

  .flipbook .button {
    display: none;
  }

  .flipbook .action-bar {
    position: absolute;
    z-index: 10;
    bottom: 0;
    left: 0;
    right: 0;
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
