<template>
    <div class="flex flex-col w-screen h-screen py-8 gap-x-2 gap-y-1 text-center items-center justify-center font-mono text-slate-300">
        <div className="flex flex-col items-center">
            <a className="items-center justify-center p-3" href='./raymondLewis.pdf' target="_blank">
              <button className="bg-red-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mb-3">
                Download Pdf
              </button>
                <img :src="Resume" />

            </a>
          </div>

    </div>

</template>

<script>
import Resume from '../assets/blah.png';

    export default {
        name:"MyResume",
        data(){
            return{
                Resume,
            }
        }
    }
</script>

<style scoped>
img{
    height: 85vh;
}
</style>