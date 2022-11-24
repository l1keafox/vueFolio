<template>
  <div id="NavMenu" class=" text-slate-900 font-josefin">

    <TransitionRoot
      :show="showMenu"
      enter="transition ease-in-out duration-1500 transform"
      enter-from="-translate-x-full"
      enter-to="translate-x-0"
      leave="transition ease-in-out duration-1500 transform"
      leave-from="translate-x-0"
      leave-to="-translate-x-full"    
    >
      <ol id="menuOne" class="absolute left-1 top-1">
        <li @click="$emit('navClick','AboutMe')">About Me</li>
        <li @click="$emit('navClick','ContactMe')">Contact Me</li>
      </ol>
    </TransitionRoot>

    <TransitionRoot
      :show="showMenu"
      enter="transition ease-in-out duration-1500 transform"
      enter-from="-translate-x-full"
      enter-to="translate-x-0"
      leave="transition ease-in-out duration-1500 transform"
      leave-from="translate-x-0"
      leave-to="-translate-x-full"    
    >

    <ol id="menuTwo" class="absolute right-1 top-1">
        <li @click="$emit('navClick','MyPortfolio')">Portfolio</li>
        <li @click="$emit('navClick','MyResume')">Resume</li>
       </ol>
    </TransitionRoot>

</div>
</template>

<script>
//import { Transition } from "vue";
import { TransitionRoot } from "@headlessui/vue";

export default {
  name: "NavMenu",
  emits:['navClick'],
  data() {
    return {
      showMenu: false,
      showButton:false
    };
  },
  mounted(){
    this.showMenu = true;
  },
  methods: {
    toggleMenu() {
      this.showMenu = !this.showMenu;
      // setTimeout(() => {
      //     console.log('triggered showMenu')
      // }, 500);
    },
    navStage(newStage){
            console.log("Nav Bar Stage change into:",newStage)
    }
  },
  components: {
    TransitionRoot,
  },
};
</script>

<style scoped>
#menuOne li {
  margin: 5px;
  padding: 5px;
  margin-top:15px;
  width: 200px;
  border: 1px solid blue;
  background-color: rgb(224, 24, 181);
  text-align: right;
  cursor: pointer;
}
#menuTwo li {
    margin: 5px;
    padding: 5px;
    margin-top:15px;
    width: 200px;
    border: 1px solid blue;
    background-color: rgb(177, 14, 14);
    text-align: left;
    cursor: pointer;
  }
  

</style>
