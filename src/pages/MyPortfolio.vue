<template>
  <div class="flex flex-col w-screen h-screen text-center items-center justify-center font-mono text-slate-300">
    <h1 class="text-7xl font-bold pb-5"> {{Portfolios[pIndex].title}}</h1>
    <div class="w-9/12 flex h-1/2 justify-between ">
      <button @click="indexLeft" class="bg-slate-700 p-3">left</button>
      <div class="flex flex-col px-10">
        <div class="flex  items-center justify-center ">
            <img class="w-[40rem]" :src='Portfolios[pIndex].img' alt=""/>
            <div class="flex flex-col w-1/2 text-xl">
                <p class="text-xl">  {{Portfolios[pIndex].description}} </p>
                <hr/>
                <br/>
                <div class="flex items-center justify-around">
                    <a :href="Portfolios[pIndex].repoLink" class="bg-yellow-900 p-2 border-2 border-green-300"> Repo </a>
                    <a :href="Portfolios[pIndex].deployLink"> deployLink </a>
                </div>
            </div>
        </div>
        </div>
      <button class="bg-slate-700 p-3" @click="indexRight">right</button>
    </div>
  </div>
</template>

<script>
import reactFolio from './../assets/bubble.png';
import middle from './../assets/bubble.png';
import projectOne from './../assets/bubble.png';
import htmlFolio from './../assets/bubble.png';
// import reactFolio from './../assets/reactfolio.png';
// import middle from './../assets/middle.png';
// import projectOne from './../assets/projectOne.png';
// import htmlFolio from './../assets/htmlFolio.png';

import bubble from './../assets/bubble.png';

import vuefolio from './../assets/bubble.png';
import team from './../assets/bubble.png';
import weather from './../assets/bubble.png';
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
          deployLink: "https://l1keafox.github.io/reactFolio/",
        },
        {
          title: "Professional React Portfolio Mk.II",
          description:
            "My second portfolio made at the end of the bootcamp in Oct of 2022. It uses React, Material UI, tailwind and headless ui.",
          img: reactFolio,
          repoLink: "https://github.com/l1keafox/Rayfolio",
          deployLink: "https://l1keafox.github.io/Rayfolio/",
        },
        {
          title: "My First Portoflio",
          description:
            "Made in first two weeks of bootcamp made in Sept of 2022, using only HTML/CSS/JS with no frame work.",
          img: htmlFolio,
          repoLink: "https://github.com/l1keafox/reactFolio",
          deployLink: "https://l1keafox.github.io/reactFolio/",
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
