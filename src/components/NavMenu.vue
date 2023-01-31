<template>
  <div id="NavMenu" class=" text-slate-900 font-josefin fixed">

    <TransitionRoot
      :show="showMenu"
      enter="transition-opacity duration-[1500ms]"
      enter-from="opacity-0"
      enter-to="opacity-100"
      leave="transition-opacity duration-[1500ms]"
      leave-from="opacity-100"
      leave-to="opacity-0"
    >
    
        <button @click="$emit('navClick','AboutMe')" :class=" buttonOneClass" class = "btn" > <div data-value="About me"  @mouseover="doThis">About me</div> <AccountQuestion class="ml-5"/> </button>
        <button @click="$emit('navClick','MyPortfolio')"  :class="buttonTwoClass" class = "btn" > <div data-value="Portfolio"  @mouseover="doThis"> Portfolio </div><Briefcase class="ml-5"/></button>
        <button @click="$emit('navClick','MyResume')"   :class="buttonThreeClass" class = "btn" > <div data-value="Resume"  @mouseover="doThis">Resume </div><FileDocument class="ml-5"/></button>
        <button @click="$emit('navClick','ContactMe')" :class="buttonFourClass" class = "btn" ><div data-value="Contact Me"  @mouseover="doThis">Contact Me </div><CardAccountPhoneOutline class="ml-5"/></button>

    </TransitionRoot>

</div>
</template>

<script>
//import { Transition } from "vue";
import { TransitionRoot } from "@headlessui/vue";
import CardAccountPhoneOutline from 'vue-material-design-icons/CardAccountPhoneOutline.vue';
import Briefcase from 'vue-material-design-icons/Briefcase.vue';
import FileDocument from 'vue-material-design-icons/FileDocument.vue';
import AccountQuestion from 'vue-material-design-icons/AccountQuestion.vue';

export default {
  name: "NavMenu",
  components: {
    TransitionRoot,
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
      toggleShowMenu:true,
      // buttonOneClass:'flex  justify-end  bg-yellow-300 absolute -left-48 top-1 hover:-left-1',
      // buttonTwoClass:'flex  justify-end  bg-yellow-300 absolute -left-48 top-20 hover:-left-1',
      // buttonThreeClass:'flex  justify-end  bg-yellow-300 absolute -left-48 top-40 hover:-left-1',
      // buttonFourClass:'flex  justify-end  bg-yellow-300 absolute -left-48 top-60 hover:-left-1',
      buttonOneClass :'flex  justify-end  bg-yellow-300 absolute -left-1 top-1',
      buttonTwoClass : 'flex  justify-end  bg-yellow-300 absolute -left-1 top-20 hover:-left-1',
      buttonThreeClass : 'flex  justify-end  bg-yellow-300 absolute -left-1 top-40 hover:-left-1',
      buttonFourClass : 'flex  justify-end  bg-yellow-300 absolute -left-1 top-60 hover:-left-1',
    
    };
  },
  mounted(){
    this.showMenu = true;
    setTimeout(() => {
      this.showMenus();
    }, 2000);

		let docu = document.getElementsByClassName("btn");
    console.log(docu.length);
    // docu.forEach(doc=>{
    //   console.log(doc);
    //   doc.onmouseover = (event)=>{
    //     console.log(event);
    //   }
    // })
    //button

  },
  methods: {
    doThis(event){
		// const letters = "ABCEDFGHIJKLMNOPQRSTUVWXYZ";
    const letters = "abcdefghijklmnopqrstuvwxyz";
    console.log(event);
		let iterations = 0;
		const interval = setInterval(() => {
			event.target.innerText = event.target.innerText
				.split("")
				.map((letter, index) => {
					if (index < iterations) {
						return event.target.dataset.value[index];
					}
					return letters[Math.floor(Math.random() * 26)];
				})
				.join("");
			if (iterations >= event.target.innerText.length) clearInterval(interval);
			iterations += 1 / 3;
		}, 30);
  },  
    showMenus(){
        console.log("toggle menu");
        this.toggleShowMenu = !this.toggleShowMenu;
        if(this.toggleShowMenu){
            this.buttonOneClass ='flex  justify-end  bg-yellow-300 absolute -left-1 top-1 ';
            this.buttonTwoClass = 'flex  justify-end  bg-yellow-300 absolute -left-1 top-20 hover:-left-1';
            this.buttonThreeClass = 'flex  justify-end  bg-yellow-300 absolute -left-1 top-40 hover:-left-1';
            this.buttonFourClass ='flex  justify-end  bg-yellow-300 absolute -left-1 top-60 hover:-left-1';
        } else {
            this.buttonOneClass ='flex  justify-end  bg-yellow-300 absolute -left-48 top-1 hover:-left-1  ';
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
  background-color: rgb(24, 127, 224);
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
