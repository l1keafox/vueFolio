<template>
  <div
    class="flex flex-col w-screen h-screen py-8 gap-x-2 gap-y-1 text-center items-center justify-evenly font-mono text-slate-300"
  >
    <h1 class="text-5xl font-bold">Portfolio</h1>
    <div class="flex justify-around w-screen h-2/3">
      <button @click="indexLeft">left</button>
      <div>
        <h1> {{Portfolios[pIndex].title}}</h1>
      </div>
      
      <button @click="indexRight">right</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyPortfolio",
  methods:{
    indexLeft(){
        this.pIndex--;
        if(this.pIndex < 0){
            this.pIndex = this.Portfolios.length-1;
        }
    },
    indexRight(){
        this.pIndex++;
        if(this.pIndex >= this.Portfolios.length){
            this.pIndex = 0;
        }
    },
    currentPortfolio(){
        return this.Portfolios;
    }
  },
  data() {
    return {
      pIndex:0,
      Portfolios: [
        {
          title: "Vue Professional Portfolio",
          description:
            "This Website, made from Vue and tailwind",
          img: './../assets/reactFolio.png',
          repoLink: "https://github.com/l1keafox/vueFolio",
          deployLink: "https://l1keafox.github.io/reactFolio/",
        },
        {
          title: "React Professional Portfolio",
          description:
            "A different website that is made from scratch using React, Material UI, tailwind and headless ui.",
          img: './../assets/reactFolio.png',
          repoLink: "https://github.com/l1keafox/reactFolio",
          deployLink: "https://l1keafox.github.io/reactFolio/",
        },

        {
          title: "Bubble Dungeonz",
          description:
            "A platform for game developers to host multi/single player games to interact with other users. Features a multiplayer bubble popping game, saved chat groups and customized display settings",
          img: './../assets/reactFolio.png',
          repoLink: "https://github.com/l1keafox/bubbleDungeonz",
          deployLink: "https://bubbledungeonz.herokuapp.com/",
        },

        {
          title: "Middle-Where",
          description:
            "A web app to find a centralized location for a group of friends. Users can create accounts and login, using google maps to display location of friends and the central meeting spot. This was my second group project of six people, I conceived the idea and pushed for MVP",
          img: './../assets/reactFolio.png',
          repoLink: "https://github.com/l1keafox/middleWhere",
          deployLink: "https://limitless-temple-38712.herokuapp.com/",
        },
        {
          title: "RealTimeCommodities",
          description:
            "My first group project, taking 5 people to make. It is a web app that will pull commodities news/prices through an API call. Uses google graphs to show history of commodity prices.",
          img: './../assets/reactFolio.png',
          repoLink: "https://github.com/l1keafox/RealTimeCommodities",
          deployLink: "https://l1keafox.github.io/RealTimeCommodities/",
        },
        {
          title: "Weather DashBoard",
          description:
            "An web app just made with the front end with bootstrap, jquery and openweathermap.org for the api. It will take in cities and forecast 5 days in the future ",
          img: './../assets/reactFolio.png',
          repoLink: "https://github.com/l1keafox/weatherDashboard",
          deployLink: "https://l1keafox.github.io/weatherDashboard/",
        },
        {
          title: "Team maker",
          description:
            "A node.js application that uses inquire to ask question in the command line. Afterwards it will create an html page of the team you have entered in. ",
          img: './../assets/reactFolio.png',
          repoLink: "https://github.com/l1keafox/myTeamSetting",
          deployLink: "https://l1keafox.github.io/myTeamSetting/",
        },
      ],
    };
  },
  computed: {},
};
</script>

<style scoped></style>
