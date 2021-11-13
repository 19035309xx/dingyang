<template>

<div>
  <div class="up"><a href="#top">back</a></div>
<div id="card">
    <div id="small">
    <p id="h22">今日预测</p>
    <div id="link-top"></div>
    <p id="h33">FORECAST</p>
    </div>
    <div id="title">
    <!-- <div v-for="item in list" :key="item.id"> <p id="h44" ><el-button id="h55" @click="$router.push('/{{item.title}}')">{{item.title}} </el-button></p> -->
     <div v-for="(item,index) in list" :key="item.id" > <p class="h44"  ><a :href="'#'+na[index].num"  id="h55"  > {{item.title}} </a>
             <div id="link-top"></div>
             <!-- <div v-for="(item,index) in list" :key="item.id" > <p class="h44"  ><button @click.native="goAnchor('#'+nu[index].num)" style="background-color: black "  id="h55"  > {{item.title}} </button>
             <div id="link-top"></div> -->
    </div>

</div>


</div>

    <div  id="hole" >
        <div v-for="(item,index) in list" :key="item.id" class="fen">
       <p class="h23" :id="na[index].num" >{{item.title}}</p>
    <div id="link-top1"></div> 
     <img src="../assets/bp1.png">
       
    <p id="h24" > {{item.content}}</p>
        </div>

        

    </div>
    <el-pagination class="block222"
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
     :current-page="queryInfo.pagenum" 
      :page-sizes="[6]"
     :page-size="queryInfo.pagesize" layout="total, sizes, prev, pager, next, jumper" :total="total">
      </el-pagination>

</div>

   

     
  
</template>

<style>

.fen{
  background-color: whitesmoke;
 
  border-style: solid;
  border-width: 2px;
  margin-top: 20px;
  border-color: rgb(102, 136, 230);
  /* border-radius: 10px; */
  float: left;
  opacity: 0.9;
  box-shadow:0 1px 1px 1px rgb(165, 181, 226) ;

}
#card{
    width: 20%;
    margin-left: 10%;
    height: 560px;
    background-color: #305DC3;
    margin-top: 30px;
    
    
   
}
#small{
    background-color: #2D57B6;
    width: 100%;
    height: 135px;
}
#h22{
   
    margin-left: 20%;
    width: 50%;
    margin-top: 20px;
    float: left;
    color: #FFFFFF;
    font-size: 1.5em;

}
#h33{
    float: left;
     margin-left: 65%;
    color: #FFFFFF;
}
#link-top {
    float: left;
            width: 80%;
            height: 1px;
            border-top: solid #114f9b 1px;
            margin-left: 10%;
        }
#title{
    width: 100%;
   
    height: 430px;
}
.h44{
    margin-top: 10px;
    float: left;
    margin-left: 15%;
    font-size: 1.2em;
    background-color: #cfd5e2;

}
#h55{
    font-size: 1.1em;
    border-radius: 0;
    border: none;
    background: none;
    color: white;
    text-decoration: none;
    background-color: #305DC3;
    
}
#hole{
    width: 60%;
    /* background-color: antiquewhite; */
    margin-left: 33%;
   height: auto;
   float: left;
   margin-top: -540px;
 

    /* border-style: solid;
    border-width: 1px;
    border-color: darkgray; */
   
}
#hole img{
    width: 70%;
    margin-left: 15%;
}
.h23{
   
    margin-left: 10%;
    width: 50%;
    margin-top: 20px;
    float: left;
    color: #4b76d3;
    font-size: 30px;
    font-weight: 800;
    font-family: "新宋体";

}
#link-top1 {
    float: left;
            width: 80%;
            height: 1px;
            border-top: solid #4b4d4e 1px;
            margin-left: 10%;
            margin-top: -20px;

        }
#h24{
    float: left;
    text-indent: 2em;
    font-family: "新宋体";
    font-size: 20px;
    font-weight: 400;
    width: 90%;
    margin-left: 5%;
    color: rgb(56, 55, 55);
}
.block222{
  /* background-color: aquamarine; */
  margin-top: -560px;
 margin-left: 40%; 
 width: 50%;


 
}

.up{
  background-color: rgb(211, 209, 209);
  float: left;
  height: 70px;
 position:fixed;
    z-index:99;
  width: 70px;
 margin-top: 24%;
  border-radius: 100%;
  margin-left: 2%;

}
.up a{
  text-decoration: none;
  text-align: center;
  line-height: 3em;
  font-size: 1.5em;
  margin-left: 8px;
  font-weight: 800;
  color: rgb(46, 80, 192);
}



  
</style>
<script>


export default {
  name: 'News',
  data () {
    return {
      currentDate: new Date(),
      list:[],
      currentPage1: 5,
        currentPage2: 5,
        currentPage3: 5,
        currentPage4: 4,
        queryInfo: {
        title: '',
        type: '',
        pagenum: 1,
        pagesize: 6,
      },
      total: 0,
        na:[
          {
            num:0
          },
           {
            num:1
          },
           {
            num:2
          },
           {
            num:3
          },
           {
            num:4
          },
           {
            num:5
          },
        ]
    }
  }, 
  created () {
    this.test()
  },
  mounted(){
     this.goAnchor(selector)
  },
  methods: {
    async test(){
      const res =await this.$http.get('/dingyang/get-articles',{params:this.queryInfo})
      var listtmp=res.data.data
      // for(var i=0;i<listtmp.length;i++){
      //   if(listtmp[i].content.length>40){
      //     listtmp[i].content=listtmp[i].content.substr(0,40)
      //   }
      // }
      this.list=listtmp
       const total_server = await this.$http.get('/dingyang/get-articles-count')
      this.total = total_server.data.data[0]['COUNT(*)']
    },
    handleSizeChange(newSize) {
      //当每页最多显示的数据数表单更改时，其值(作为参数传给服务器)也要跟着改
      this.queryInfo.pagesize = newSize
      //重新向服务器发送新的参数
      this.test()
    },
    handleCurrentChange(newPage) {
      //及时更改要获取的页数
      this.queryInfo.pagenum = newPage
      this.test()
    },
 
  // goRegister1(index){
  //       console.log(index)
  //       this.$el.querySelector(index).scrollIntoView(
  //         {
  //           behavior: "smooth", // 平滑过渡
  //           block: "start" // 上边框与视窗顶部平齐
  //         }
  //       );

  //  },

// goAnchor(selector) {
//    // this.activeBtn = index;
//    // document.querySelector("#app-root").scrollTop =                      this.$el.querySelector(selector).offsetTop;
//       this.$el.querySelector(selector).scrollIntoView();
//     },
    //  handleSizeChange(val) {
    //     console.log(`每页 ${val} 条`);
    //   },
    //   handleCurrentChange(val) {
    //     console.log(`当前页: ${val}`);
    //   },


    //   goAnchor(selector) {
    //   this.$el.querySelector(selector).scrollIntoView({
    //       behavior: "smooth",  // 平滑过渡
    //       // block:    "start"  // 上边框与视窗顶部平齐。默认值
    //   });
    // }



 },

 
}
</script>
