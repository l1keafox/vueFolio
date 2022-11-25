<template>
  <div id="NavMenu" class=" text-slate-900 font-josefin overflow-hidden">

    <TransitionRoot
      :show="showMenu"
      enter="transition-opacity duration-[1000ms]"
      enter-from="opacity-0"
      enter-to="opacity-100"
      leave="transition-opacity duration-[1000ms]"
      leave-from="opacity-100"
      leave-to="opacity-0"
    >
    <MenuIcon @click="showMenus" class="absolute top-5 cursor-pointer hover:bg-slate-500"/>
    </TransitionRoot>


    <!-- <ol id="menuOne" class="absolute -left-48 top-1">
        <ol id="menuTwo" class="absolute -right-40 top-1"> -->
        <button @click="$emit('navClick','AboutMe')" :class="buttonOneClass"> About Me <AccountQuestion class="ml-5"/> </button>
        <button @click="$emit('navClick','ContactMe')" :class="buttonTwoClass">Contact Me <CardAccountPhoneOutline class="ml-5"/></button>
        <button @click="$emit('navClick','MyPortfolio')"  :class="buttonThreeClass"> Portfolio <Briefcase class="ml-5"/></button>
        <button @click="$emit('navClick','MyResume')"  :class="buttonFourClass"> Resume <FileDocument class="ml-5"/></button>


</div>
</template>

<script>
//import { Transition } from "vue";
import { TransitionRoot } from "@headlessui/vue";
import MenuIcon from 'vue-material-design-icons/Menu.vue';   
import CardAccountPhoneOutline from 'vue-material-design-icons/CardAccountPhoneOutline.vue';
import Briefcase from 'vue-material-design-icons/Briefcase.vue';
import FileDocument from 'vue-material-design-icons/FileDocument.vue';
import AccountQuestion from 'vue-material-design-icons/AccountQuestion.vue';

export default {
  name: "NavMenu",
  components: {
    TransitionRoot,
    MenuIcon,
    CardAccountPhoneOutline,
    Briefcase,
    FileDocument,
    AccountQuestion
  },

  emits:['navClick'],
  data() {
    return {
      showMenu: false,
      showButton:false,
      toggleShowMenu:false,
      buttonOneClass:'flex  justify-end  bg-yellow-300 absolute -left-48 top-1 hover:-left-1',
      buttonTwoClass:'flex  justify-end  bg-yellow-300 absolute -left-48 top-20 hover:-left-1',
      buttonThreeClass:'flex  justify-end  bg-yellow-300 absolute -left-48 top-40 hover:-left-1',
      buttonFourClass:'flex  justify-end  bg-yellow-300 absolute -left-48 top-60 hover:-left-1',
    
    };
  },
  mounted(){
    this.showMenu = true;
  },
  methods: {
    showMenus(){
        console.log("toggle menu");
        this.toggleShowMenu = !this.toggleShowMenu;
        if(this.toggleShowMenu){
            this.buttonOneClass ='flex  justify-end  bg-yellow-300 absolute -left-1 top-1';
            this.buttonTwoClass = 'flex  justify-end  bg-yellow-300 absolute -left-1 top-20 hover:-left-1';
            this.buttonThreeClass = 'flex  justify-end  bg-yellow-300 absolute -left-1 top-40 hover:-left-1';
            this.buttonFourClass ='flex  justify-end  bg-yellow-300 absolute -left-1 top-60 hover:-left-1';
        } else {
            this.buttonOneClass ='flex  justify-end  bg-yellow-300 absolute -left-48 top-1 hover:-left-1';
            this.buttonTwoClass = 'flex  justify-end  bg-yellow-300 absolute -left-48 top-20 hover:-left-1';
            this.buttonThreeClass = 'flex  justify-end  bg-yellow-300 absolute -left-48 top-40 hover:-left-1';
            this.buttonFourClass ='flex  justify-end  bg-yellow-300 absolute -left-48 top-60 hover:-left-1';
        }
    },  
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
};
</script>

<style scoped>
NavMenu{
    width: 100vw;
}


button {
  margin: 5px;
  padding: 5px;
  margin-top:15px;
  width: 220px;
  border: 1px solid blue;
  background-color: rgb(224, 24, 181);
  text-align: left;
  cursor: pointer;
  transition: all 0.5s linear;
}
  

</style>
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
