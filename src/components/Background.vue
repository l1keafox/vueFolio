<template>
    <div id="backGround">
        <div id="blueSplit" > </div>
        <div id="greyParent">
          <div id="greySplitTop">  </div>
          <div id="greySplitMiddle">  </div>
          <div id="greySplitBottom" >  </div>
        </div>
      </div>
    </template>

<script>
    export default {
        name:"BackGround"    
    }
</script>

<style scoped>
*{
    transition: all .1s linear;
  }
  
#backGround{
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw;
    z-index: -10000;
  }
  #blueSplit{
    position: relative;
    height: 1500px;
    width: 100%;
    top:-900px;
    background-color:rgb(47,184,203);
    transform: skew(0deg,-5deg);
    z-index: -10000;
  }
  
  #greyParent{
    position: relative;
    width:100%;
    top:-600px;
    z-index: -10000;
  }
  #greySplitTop{
    position: relative;
    width:100%;
    height: 500px;
    top:100px;
    background-color: rgb(226,226,226);
    transform: skew(0deg,5deg);
  }
  #greySplitMiddle{
    position: relative;
    width:100%;
    top:-120px;
    height: 350px;
    background-color: rgb(226,226,226);
  }
  #greySplitBottom{
    position: relative;
    width:100%;
    height: 500px;
    top:-350px;
    background-color: rgb(226,226,226);
    transform: skew(0deg,-5deg);
  }
</style>