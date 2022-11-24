<template>
  <div id="tiles">Hey</div>
</template>

<script>
import anime from 'animejs/lib/anime.es.js';
export default {
  name: "App",
  components: {},
  data() {
    return {};
  },
  mounted() {
    let toggle = false;
    let wrapper = document.getElementById("tiles");
    let columns = Math.floor(document.body.clientWidth / 50);
    let rows = Math.floor(document.body.clientWidth / 50);

    const handleOnClick = index => {
    // count = count + 1;
    console.log('click');
    toggle = !toggle;
    anime({
      targets:  ".tile",
      opacity: toggle ? 0 : 1,
      // backgroundColor: colors[count % (colors.length -1)],
      delay: anime.stagger(50,{
          grid:[columns,rows],
          from:index
      })
    })

  }    
    const createTile = (index) => { //
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
  --g1:rgb(15, 129, 62);
  --g2:rgb(122, 10, 46);
}
@keyframes background-pan {
  from {
    background-position: 0% center;
  }
  to{
    background-position: -200% center;
  }
}

body {
  animation: background-pan 10s linear infinite;
  background: linear-gradient(
  to right,
  var(--g1),
  var(--g2),
  var(--g1)
  );
  background-size: 200%;
}
#tiles{
  height:100vh;
  width:100vw;
  display:grid;
  grid-template-columns:repeat(var(--columns), 1fr);
  grid-template-rows: repeat(var(--rows), 1fr);
}
.tile{
  
  position: relative;
}
.tile:hover{
  opacity: 0.95;
}
.tile:before {
  background-color : rgb(20,20,20);
  content: "";
  position: absolute;
  inset: 0.5px;

}
</style>
