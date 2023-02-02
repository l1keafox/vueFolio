<template>
  <div class="tile">
    <img  data-nav="1" src="https://images.unsplash.com/photo-1670022326053-74ee3cdc1cc0?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=687&q=80"/>
  </div> 
  


    <!-- <div id="aboutMe" class="flex flex-col py-8 gap-x-2 gap-y-1 text-center items-center justify-center font-mono text-slate-300 bg-yellow-300 w-96 h-14" > 
      <div class="w-4/5 mx-auto ">
             <div class="flex justify-center items-center space-x-16 text-5xl font-noto dark:text-slate-400">
              <p>
                I am a<span class="text-green-400"> full stack </span>software
                engineer with a background in
                <span class="text-red-600">malware</span> research. I enjoy
                the process of creating programs, websites, clothes and
                relationships.
              </p>
            </div>
            <br/>
            <p className="text-5xl block relative text-center font-ubuntu  dark:text-slate-400">
                my skillset
              </p>
              <br/>
            <div class="flex items-center justify-center">
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/html5.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/react.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/bootstrap.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/mysql.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/mongodb.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/socketdotio.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/graphql.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/tailwindcss.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/handlebarsdotjs.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/typescript.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/github.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/nodedotjs.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/npm.svg" />   
            <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/vuedotjs.svg" />   
            </div>
          </div> 

      </div> -->
</template>

<script>
// import { Transition } from "vue";

    export default {
        name:"HomePage",
        components:{
          
          
        },
        data(){
            return{
              showHome:false,
              showMenu:false
            }
        },
        methods:{
        },
        mounted(){
//           this.showHome = true;
        },
        updated(){
          console.log('udated');
        }
    }
</script>

<style scoped>


.tile{
  position: absolute;
  left: 30%;
  top: 40%;  
}
.tile > img{
  height: 100%;
  width: 100%;
  object-fit:cover;
  border-radius:inherit;
  height: 15%;
  width:25% ;
}
</style>
position: absolute;
height: 15%;
width:25% ;

