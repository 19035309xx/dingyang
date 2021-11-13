<template>
<div id="top">
      <img src='../assets/7e68927951d67770c3ae2256e909d49.png' >
    <el-menu :default-active="activeIndex2"
  class="el-menu-demo"
  mode="horizontal"
  @select="handleSelect"
  background-color="white"
  
  active-text-color="#305DC3" router >
  <el-menu-item index="/main">首页</el-menu-item>
   <el-menu-item index="/forecast">今日预测</el-menu-item>
    <el-menu-item index="/stock">股市人生</el-menu-item>
     <!-- <el-menu-item index="/report">月度报告</el-menu-item> -->
      <!-- <el-menu-item index="/Investigation">实地调查</el-menu-item> -->
       <el-menu-item index="/investment">投资哲学</el-menu-item>
        <el-menu-item index="/Investigation">其他文章</el-menu-item>
         <!-- <el-menu-item index="/About">关于丁洋</el-menu-item> -->
 
  
</el-menu>

</div>


</template>
<script>
  export default {
    data() {
      return {
        activeIndex: '1',
        activeIndex2: '1'
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }</script>

  <style >
  #top img{
    width: 15%;
    margin-left: 5%;
  }
  .el-menu{
    width: 65%;
    float:right;
    
    font-weight: 700;
    color: rgb(77, 75, 75);
    
  }
  .el-menu-item{
    width: 12.5%;
    text-align: center;
  }

  
  </style>