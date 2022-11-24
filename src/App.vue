<template>
  <div id="tiles" class=""></div>
  <div id="content" class="text-3xl absolute" v-if="introDone">
    <NavMenu @navClick="navStage"/>
    <component :is="this.currentStage" />

  </div>
  <div id="welcome" class="text-3xl absolute pointer-events-none" v-if="introDone === false">
    <TransitionRoot
      :show="isShowing"
      enter="transition-opacity duration-[1000ms]"
      enter-from="opacity-0"
      enter-to="opacity-100"
      leave="transition-opacity duration-[1000ms]"
      leave-from="opacity-100"
      leave-to="opacity-0"
    >
      <LandingPage />
    </TransitionRoot>
  </div>
</template>

<script>
import anime from "animejs/lib/anime.es.js";
import LandingPage from "./pages/LandingPage";
import HomePage from "./pages/HomePage";
import { TransitionRoot } from "@headlessui/vue";
import NavMenu from "./components/NavMenu" 

import AboutMe from "./pages/AboutMe";
import ContactMe from "./pages/ContactMe";
import MyResume from "./pages/MyResume";
import MyPortfolio from "./pages/MyPortfolio";


export default {
  name: "App",
  components: {
    HomePage,
    LandingPage,
    TransitionRoot,
    MyResume,
    MyPortfolio,
    AboutMe,
    ContactMe,
    NavMenu
  },
  data() {
    return {
      introDone: false,
      isShowing: false,
      currentStage:''
    };
  },
  methods:{
    navStage(newstage){
      console.log('changing stage into:',newstage);
      this.currentStage = newstage;
    }
  },  
  mounted() {
    let toggle = false;
    this.isShowing = true;
    let wrapper = document.getElementById("tiles");
    let columns = Math.floor(document.body.clientWidth / 50);
    let rows = Math.floor(document.body.clientWidth / 50);
    this.currentStage = "LandingPage";
    const handleOnClick = (index) => {
      this.isShowing = false;
      toggle = !toggle;
      this.currentStage = "HomePage";
      let tiles = document.getElementsByClassName("tile");
      console.log("Remove grid and ready folio");
      for (let tile of tiles) {
        tile.onclick = null;
      }
      window.onresize = null;
      anime({
        targets: ".tile",
        opacity: toggle ? 0 : 1,
        delay: anime.stagger(50, {
          grid: [columns, rows],
          from: index,
        }),
      });

      setTimeout(() => {
        this.introDone = !this.introDone;
      }, 1000);
    };
    const createTile = (index) => {
      //
      const tile = document.createElement("div");
      tile.classList.add("tile");
      tile.onclick = () => handleOnClick(index);
      return tile;
    };

    const createTiles = (quantity) => {
      Array.from(Array(quantity)).map((tile, index) => {
        wrapper.appendChild(createTile(index));
      });
    };
    const createGrid = () => {
      wrapper.innerHTML = "";
      columns = Math.floor(document.body.clientWidth / 50);
      rows = Math.floor(document.body.clientHeight / 50);
      wrapper.style.setProperty("--columns", columns);
      wrapper.style.setProperty("--rows", rows);
      createTiles(columns * rows);
      console.log(
        columns,
        rows,
        document.body.clientWidth,
        document.body.clientHeight
      );
    };
    createGrid();
    window.onresize = () => createGrid();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #5d6063;
}
:root {
  --g1: rgb(107, 96, 201);
  --g2: rgb(122, 10, 46);
}
@keyframes background-pan {
  from {
    background-position: 0% center;
  }
  to {
    background-position: -200% center;
  }
}
#content {
  display: fixed;
  left: 0%;
  top: 0%;
}
#welcome {
  display: fixed;
  left: 0%;
  top: 0%;
}

body {
  animation: background-pan 10s linear infinite;
  background: linear-gradient(to right, var(--g1), var(--g2), var(--g1));
  background-size: 200%;
}
#tiles {
  height: 100vh;
  width: 100vw;
  display: grid;
  grid-template-columns: repeat(var(--columns), 1fr);
  grid-template-rows: repeat(var(--rows), 1fr);
}
.tile {
  position: relative;
}
.tile:hover {
  opacity: 0.95;
  cursor: pointer;
}
.tile:before {
  background-color: rgb(20, 20, 20);
  content: "";
  position: absolute;
  inset: 1px;
}
</style>
