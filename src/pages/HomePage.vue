<template>


  <div class="flex flex-col  h-screen py-8 gap-x-2 gap-y-1 text-center items-center justify-center font-mono text-slate-300" >
      <Transition name="fade">
        <div v-if="showHome" class="w-4/5 mx-auto ">
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
        </Transition>

      </div>
</template>

<script>
import { Transition } from "vue";

    export default {
        name:"HomePage",
        components:{
          Transition,
          
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
           this.showHome = true;
        },
        updated(){
          console.log('udated');
        }
    }
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

</style>