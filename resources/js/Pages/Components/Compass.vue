<script setup>
  import { onMounted } from 'vue';
  import { isMobile } from '@/app.js';


  function followMouseCursor(){
    // let needle = document.querySelector("#needle");
    // let background = document.querySelector("#background");
    
    // background.addEventListener("mousemove", e => {
    //     let backgroundBoundingRect = background.getBoundingClientRect();
    //     let backgroundCenter = {
    //         x: backgroundBoundingRect.left + backgroundBoundingRect.width / 2,
    //         y: backgroundBoundingRect.top + backgroundBoundingRect.height / 2
    //     };

    //     let angle = Math.atan2(e.clientX - backgroundCenter.x, - (e.clientY - backgroundCenter.y)) * (180 / Math.PI);
    //     needle.style.transform = `translate(-50%, -50%) rotate(${angle}deg)`;  
    // })
    let needle = document.querySelector("#needle");
    
    document.addEventListener("mousemove", e => {
        let pageCenter = {
            x: window.innerWidth / 2,
            y: window.innerHeight / 2
        };

        let angle = Math.atan2(e.clientX - pageCenter.x, - (e.clientY - pageCenter.y)) * (180 / Math.PI);
        needle.style.transform = `translate(-50%, -50%) rotate(${angle}deg)`;  
    })
  }

  // function showInConsole(e){
  //     // anime({
  //     //   targets: '#compass',
  //     //   rotate: 5,
  //     //   scale: 1,
  //     //   loop: true,
  //     // });
  //     setTimeout(() => {
  //         console.log(e.clientX, e.clientY);
          
  //     }, 2000);
  // }

  onMounted(() => { 
    if (!isMobile()) {
      followMouseCursor(); 
    }
  })
</script>

<template>
  <div v-if="!isMobile()" id="background" class="flex justify-center items-center">
    <img id="compass" src="images/compass.svg" alt="Compass image">
    <div id="needle">
      <!-- i need create the needle with css border -->
      <div id="red-tip"></div>
      <div id="black-tip"></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>


    #background{
      position: relative;
      margin: 0;
      padding: 0;
      max-width: 25vw;
      #compass{
        max-width: 100%;
        border-width: 1px;
        border-radius: 50%;
        border-color: #fff;
        // padding: 1rem;
        background-color: #fff;
  
      }
      #needle{
        position: absolute;
        top: 50%;
        left: 51.5%;
        transform: translate(-53%, -50%);
        // left: calc(12rem / 2 - 0.4rem);
        // left: 50%;
        // top: 50%;
        // transform: translate(-50%,-50%);
        // left: 46.5%;
        // transform: translate(-46.5%, -12.8%);
        // display: flex;
        // justify-content: center;
        // align-items: center;
        #red-tip{
          width: 0;
          height: 0;
          border-left: 0.6rem solid transparent;
          border-right: 0.6rem solid transparent;
          border-bottom: 5rem solid #b2140f;
          transition: border-bottom-width 0.5s ease, border-top-width 0.5s ease, border-left-width 0.5s ease, border-right-width 0.5s ease;
        };
        #black-tip{
          width: 0;
          height: 0;
          border-left: 0.6rem solid transparent;
          border-right: 0.6rem solid transparent;
          border-top: 5rem solid #343434;
        }

        @media screen and (min-width: 80rem) {
          :is(#red-tip, #black-tip){
            border-left-width: 0.9rem;
            border-right-width: 0.9rem;
          }
          #red-tip{
            border-bottom-width: 7.5rem;
          }
          #black-tip{
            border-top-width: 7.5rem;
          }
        }

        @media screen and (min-width: 100rem) {
          :is(#red-tip, #black-tip){
            border-left-width: 1.2rem;
            border-right-width: 1.2rem;
          }
          #red-tip{
            border-bottom-width: 10rem;
          }
          #black-tip{
            border-top-width: 10rem;
          }
        }

        @media screen and (min-width: 150rem) {
          :is(#red-tip, #black-tip){
            border-left-width: 1.5rem;
            border-right-width: 1.5rem;
          }
          #red-tip{
            border-bottom-width: 15rem;
          }
          #black-tip{
            border-top-width: 15rem;
          }
        }

        @media screen and (min-width: 200rem) {
          :is(#red-tip, #black-tip){
            border-left-width: 1.8rem;
            border-right-width: 1.8rem;
          }
          #red-tip{
            border-bottom-width: 20rem;
          }
          #black-tip{
            border-top-width: 20rem;
          }
        }
      }
    }
</style>
