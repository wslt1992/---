<template>
  <div id="app">
    <!-- <main-page></main-page> -->
      <transition
          
          name="custom-classes-transition"
          :enter-active-class="transitionInName"
          :leave-active-class="transitionOutName"
            >
    <!-- <keep-alive include="mainpage"> -->
    <keep-alive>
        <router-view></router-view>
    </keep-alive>
      </transition>
  </div>
</template>

<script>
          // mode="out-in"
                // mode="out-in"

import MainPage from './views/MainPage'
export default {
  name: 'App',
  data() {
    return {
    transitionInName:'',
    transitionOutName:''
    // transitionInName:'animated slideInRight',
    // transitionOutName:'animated slideOutLeft'
    }
  },
  components:{
    'main-page':MainPage,
  },
  methods: {
    /**
     * 监听文件
     */
    initKeyEventback() {
      let _this = this;
      // document.addEventListener("plusready", function () {
      //   plus.key.addEventListener("backbutton", function () {
      //       // alert("BackButton Key pressed!");
      //       _this.$router.back();
      //     });
      //   });
    }
  },
  mounted(){
    this.initKeyEventback()
  },
  watch: {
  '$route' (to, from) {
    // if(this.$global.isRouterForward){
    //   this.transitionInName =  'animated animated1 slideInRight'
    //   this.transitionOutName = 'animated animated1 animated-delay slideOutLeft' 
    // }else{
    //   this.transitionInName = 'animated  animated1 slideInLeft' 
    //   this.transitionOutName = 'animated animated1 animated-delay slideOutRight'
    // }
    if(this.$global.isRouterForward){
      this.transitionInName =  'animated animated1 slideInRight'
      this.transitionOutName = 'animated animated1 animated-delay slideOutLeft' 
    }else{
      this.transitionInName = 'animated  animated1 slideInLeft' 
      this.transitionOutName = 'animated animated1 animated-delay slideOutRight'
    }
    // 默认为true
    this.$global.isRouterForward  = true;
  }
}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
}
.animated.animated1{
  -webkit-animation-duration: 0.3s;
  animation-duration: 0.3s;
  -webkit-animation-fill-mode: both;
  animation-fill-mode: both;
  /* -moz-animation-duration: 0.5s; */
  /* -webkit-animation-duration:  */
  position:absolute;
  top:0
}
.animated-delay{
  /* animation-delay: 3.3s; */
}
</style>
