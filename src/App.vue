<template>
  <div id="tiles" class=""></div>
  <div id="content" class="text-3xl absolute overflow-hidden" v-if="introDone" >
    <div  class="contentSection">
      <HomePage />
    </div>

    <!-- <div id="navMenu">
      <NavMenu @navClick="scrollToRef" />
    </div>
    <div ref="AboutMe" class="contentSection">
      <AboutMe />
    </div >
    <div ref="MyPortfolio"  class="contentSection">
      <MyPortfolio />
    </div>
    <div ref="MyResume"  class="contentSection">
      <MyResume />
    </div>
    <div ref="ContactMe"  class="contentSection">
      <ContactMe />
    </div> -->
  </div>
  <div
    id="welcome"
    class="text-3xl pointer-events-none"
    v-if="introDone === false"
  >
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
import { TransitionRoot } from "@headlessui/vue";
// import NavMenu from "./components/NavMenu";
import HomePage from "./pages/HomePage";

// import AboutMe from "./pages/AboutMe";
// import ContactMe from "./pages/ContactMe";
// import MyResume from "./pages/MyResume";
// import MyPortfolio from "./pages/MyPortfolio";

export default {
  name: "App",
  components: {
    LandingPage,
    TransitionRoot,
    HomePage,
    // MyResume,
    // MyPortfolio,
    // AboutMe,
    // ContactMe,
    // NavMenu,
  },
  data() {
    return {
      introDone: false,
      isShowing: false,
      currentStage: "",
    };
  },
  methods: {
    navStage(newstage) {
      console.log("changing stage into:", newstage);
      this.currentStage = newstage;
    },
    scrollToRef(refName) {
      console.log("Scroll or ref", refName);
      let element = this.$refs[refName];
      let top = element.offsetTop;
      window.scrollTo({
        top,
        left: 0,
        behavior: "smooth",
      });
    },
  },
  updated(){
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        // console.log(entry, entry.isIntersecting);
        if (entry.isIntersecting) {
          entry.target.classList.add("show");
        } else {
          entry.target.classList.remove("show");
        }
      });
    });
    const hidden = document.querySelectorAll(".contentSection");
    hidden.forEach((el) => observer.observe(el));

  },
  mounted() {


    window.onmousemove = (e) => {
      // get mouse posistion
      if(this.introDone){
      const gallery = document.getElementById("content");
    //  console.log(gallery);
      const mouseX = e.clientX,
        mouseY = e.clientY;
      // divid by height
      const xDecimal = mouseX / window.innerWidth,
        yDecimal = mouseY / window.innerHeight;
      // multiply by gallery heigh
      const panX = gallery.offsetWidth * xDecimal * -1 * 0.5,
        panY = gallery.offsetHeight * yDecimal * -1 * 0.5;
      // set up translate
//      console.log(panX, panY);
      gallery.animate(
        {
          transform: `translate(${panX}px,${panY}px)`,
        },
        {
          duration: 4000,
          fill: "forwards",
          easing: "ease",
        }
      );
      }
    };


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
  --g1: rgb(72, 72, 73);
  --g2: rgb(21, 10, 122);
}
.contentSection {
  opacity: 0;
  filter: blur(5px);
  transition: all 0.5s;
  transform: translateY(100%);
  height: 85vh;
}
.show {
  opacity: 1;
  filter: blur(0);
  transform: translateY(0);
}
@media(prefers-reduced-motion){
  .contentSection{
    transition:none;
  }
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
#navMenu{
  z-index: 10000;
  position: fixed;
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
