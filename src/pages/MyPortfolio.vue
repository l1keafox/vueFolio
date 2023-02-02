<template>
  <div class="flex flex-col w-screen h-[40rem] text-center items-center justify-center font-noto text-slate-300 bg-blue-300">
    <h1 class="text-7xl font-bold pb-5 text-black"> {{Portfolios[pIndex].title}}</h1>
    <div class="w-9/12 flex h-2/3 bg-blue-400 rounded">
            <img class="w-1/2 rounded" :src='Portfolios[pIndex].img' alt=""/>
            <div class="flex flex-col items-center justify-around w-1/2">
              <p class="text-xl h-1/2 flex items-center justify-around p-4">  {{Portfolios[pIndex].description}} </p>
              <div class ="h-1/2 w-full flex items-center justify-around">
                <a :href="Portfolios[pIndex].repoLink" class="bg-red-400 rounded text-lg p-2 border-2 border-blue-300 text-black w-1/3"> Git Repo </a>
                <a :href="Portfolios[pIndex].deployLink" class="bg-green-400 rounded text-lg p-2 border-2 border-blue-300 text-black w-1/3"> Deployed Link </a>
              </div>
            </div>

    </div>
    <div class = "flex pt-3 w-1/3 justify-around">
      <button @click="indexLeft" class="bg-slate-600 p-3 rounded-lg"> &lt;&lt; </button> 
      <button class="bg-slate-600 p-3 rounded-lg" @click="indexRight"> >> </button> 
    </div>
  </div>
</template>

<script>
import reactFolio from './../assets/react.png';
import middle from './../assets/mid.png';
import projectOne from './../assets/one.png';
import htmlFolio from './../assets/html.png';
// import reactFolio from './../assets/reactfolio.png';
// import middle from './../assets/middle.png';
// import projectOne from './../assets/projectOne.png';
// import htmlFolio from './../assets/htmlFolio.png';

import bubble from './../assets/bubble.png';
import vuefolio from './../assets/vue.png';
import team from './../assets/team.png';
import weather from './../assets/weather.png';
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
          title: "Professional Vue Portfolio Mk.III",
          description:
            "My Third portfolio website made in November of 2022. This uses from Vue and tailwind",
          img: vuefolio,
          repoLink: "https://github.com/l1keafox/vueFolio",
          deployLink: "https://gorgeous-sorbet-b95f3f.netlify.app/",
        },
        {
          title: "Professional React Portfolio Mk.II",
          description:
            "My second portfolio made at the end of the bootcamp in Oct of 2022. It uses React, Material UI, tailwind and headless ui.",
          img: reactFolio,
          repoLink: "https://github.com/l1keafox/reactFolio",
          deployLink: "https://l1keafox.github.io/reactFolio/",
        },
        {
          title: "Portfolio Mk.I",
          description:
            "Made in first two weeks of bootcamp made in Sept of 2022, using only HTML/CSS/JS with no frame work.",
          img: htmlFolio,
          repoLink: "https://github.com/l1keafox/Rayfolio",
          deployLink: "https://l1keafox.github.io/Rayfolio/",
        },

        {
          title: "Bubble Dungeonz",
          description:
            "A platform for game developers to host multi/single player games to interact with other users. Features a multiplayer bubble popping game, saved chat groups and customized display settings",
          img: bubble,
          repoLink: "https://github.com/l1keafox/bubbleDungeonz",
          deployLink: "https://bubbledungeonz.herokuapp.com/",
        },

        {
          title: "Middle-Where",
          description:
            "A web app to find a centralized location for a group of friends. Users can create accounts and login, using google maps to display location of friends and the central meeting spot. This was my second group project of six people, I conceived the idea and pushed for MVP",
          img: middle,
          repoLink: "https://github.com/l1keafox/middleWhere",
          deployLink: "https://limitless-temple-38712.herokuapp.com/",
        },
        {
          title: "RealTimeCommodities",
          description:
            "My first group project, taking 5 people to make. It is a web app that will pull commodities news/prices through an API call. Uses google graphs to show history of commodity prices.",
          img: projectOne,
          repoLink: "https://github.com/l1keafox/RealTimeCommodities",
          deployLink: "https://l1keafox.github.io/RealTimeCommodities/",
        },
        {
          title: "Weather DashBoard",
          description:
            "An web app just made with the front end with bootstrap, jquery and openweathermap.org for the api. It will take in cities and forecast 5 days in the future ",
          img: weather,
          repoLink: "https://github.com/l1keafox/weatherDashboard",
          deployLink: "https://l1keafox.github.io/weatherDashboard/",
        },
        {
          title: "Team maker",
          description:
            "A node.js application that uses inquire to ask question in the command line. Afterwards it will create an html page of the team you have entered in. ",
          img: team,
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
