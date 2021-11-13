<template>
  <div id="app">
    
    <div class="footer">
      <span class="sp"><p class="pp"><a href="1">返回首页&nbsp;</a>|&nbsp;<a href="/other">公司介绍</a>&nbsp;|&nbsp;<a href="./other.vue">关于丁洋&nbsp;</a>|&nbsp;<a href="./other.vue">关于丁洋&nbsp;</a>&nbsp;</p></span>
      <span><p>联系我们：&nbsp; 111222333</p></span>
    </div>
  </div>
</template>

<style  scoped>
body {
  padding: 0;
  margin: 0;
}
.pp a{
  text-decoration: none;
  color: rgb(222, 225, 228);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
   

}

.footer{
  position: absolute;
  /* bottom: 0; */
  width: 100%;
  line-height: var(--footer-height);
  background: #315cd3;
  color: #fff;
  height: 80px;
  margin-top: 50px;
 
}
</style>

<script>
export default {
  name: 'vfooter',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      
    }
  }
}
</script>

<style>
/* .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
    width: 100%;
    position: absolute;
    z-index: 9999;
    bottom: 0 auto;
    margin-top: 30px;
   
  } */
</style>