<template>
    <div class="flex flex-col items-center justify-center h-screen text-slate-50 text-9xl">
        <div class="font-mono ml-5">
          RAYMOND LEWIS
        </div>
        <div class="font-mono text-xl items-end justify-end" id="ClickInfo">
            Click Anywhere
        </div>
    </div>
</template>

<script>
    export default {
        name:"LandingPage"
    }
</script>

<style scoped>
:root {
    --purple: rgb(123,31,162);
    --violet: rgb(103,58,183);
    --pink: rgb(244,143,177)
  }
  
#ClickInfo{
    -webkit-text-fill-color: rgb(184, 4, 4);
}
</style>
@keyframes background-pan {
    from {
      background-position: 0% center;
    }
    to {
      background-position: -200% center;
    }
  }
    <!-- animation: background-pan 3s linear infinite;
    background: linear-gradient(
      to right,
      var(--purple),
      var(--violet),
      var(--pink),
      var(--purple)
    );
    background-size: 200%;
    background-clip: text;
    white-space:nowrap;     -->
