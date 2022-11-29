<template>
    <div class="flex flex-col w-screen h-screen py-8 gap-x-2 gap-y-1 text-center items-center justify-center font-mono text-slate-300">
        <h1> Contact Me </h1>
        <br/>
        <div class ="flex justify-around items-center">
            <a href="tel:+13034752882" className= "flex flex-col items-center justify-center text-red-500 hover:bg-red-200"> Phone <PhoneClassic/></a>
            <a href="mailto: raymond.ed.lewis@gmail.com" className= "flex flex-col items-center justify-center text-blue-400  hover:bg-blue-100">Email <Email/></a>
            <a href="https://www.linkedin.com/in/raymond-lewis-51719325/" target="_blank" className= "flex flex-col items-center justify-center text-green-600  hover:bg-green-300">Linkedin <img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/linkedin.svg" /></a>
            <a href="https://github.com/l1keafox" target="_blank" className= "flex flex-col items-center justify-center text-yellow-300  hover:bg-yellow-100">Github<img height="32" width="32" src="https://unpkg.com/simple-icons@v7/icons/github.svg" /> </a>
        </div>
    </div>
</template>

<script>

import PhoneClassic from 'vue-material-design-icons/PhoneClassic.vue';
import Email from 'vue-material-design-icons/Email.vue';
 
    export default {
        name:"ContactMe",
        components:{
            PhoneClassic,
            Email
        }
    }
</script>

<style scoped>
a{
    padding: 5px;
}
</style>