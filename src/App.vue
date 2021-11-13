<template>
 <div id="app">
  <!-- <Ppt></Ppt> -->
  
  <Header></Header>
  <Ppt></Ppt>
 <router-view></router-view>
  <vFooter></vFooter>
 
 
</div>
</template>

<script>
import Header from './components/header.vue'
import Ppt from './components/ppt.vue'
import vFooter from './components/footer.vue'

export default {
 components:{
  Header,
  Ppt,
  vFooter
 }
 } 
</script>

<style>
  body{
      margin-top: 0px;
      margin-left:0px;
      margin-bottom: 0px;
      width: 100%;
     
      
      
  }
</style>
