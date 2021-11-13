<template>
  <div>
    <h2 style="text-align:center">{{msg}}</h2>
    <p style="text-align:center">{{msg1}}</p>
    <el-divider></el-divider>

     <!-- <el-row>
  <el-col :span="11" v-for="(item,index,j) in list" :key="j" >
    <el-card  id="control-card">
      <el-col :span="6">
          <img :src="imgsrc+(index+1)+'.jpg'" class="image">
      </el-col>
      <el-col :span="18" id="control-left1">
          <h3>{{item.title}}</h3>
          <p ><span >{{item.content}}</span></p>
          

      </el-col>
    </el-card>
  </el-col>
  
  </el-row> -->

    <el-card :span="11" v-for="(item,index,j) in list" :key="j"  id="control-card">
      <el-col :span="6">
          <img :src="imgsrc+(index+1)+'.jpg'" class="image">
      </el-col>
      <el-col :span="18" id="control-left1">
          <h3>{{item.title}}</h3>
          <p ><span v-if="item.content.length<300" >{{item.content}}</span></p>
           <p ><span v-if="item.content.length>300">{{item.content.substr(0,300)}}
             <span v-show="switchName[index].cut">{{item.content.substr(301,)}}</span>
             <span v-show="!switchName[index].cut">... ...<button class="button"  @click="toggleShopShow (index)">更多</button></span>
             <!-- <span v-show="!switchName[index].cut"></span> -->
             <span v-show="switchName[index].cut"><button class="button" @click="toggleShopShow (index)">收起</button></span>
             </span></p>
             


      </el-col>
    </el-card>

    
 
  <el-pagination class="block223"
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
     :current-page="queryInfo.pagenum" 
      :page-sizes="[6]"
     :page-size="queryInfo.pagesize" layout="total, sizes, prev, pager, next, jumper" :total="total">
      </el-pagination>


  </div>
  
</template>



<style>
  h2{
    color: rgb(27, 25, 25);
  }
  p{
    color:rgb(70, 68, 68);
    
  }
  .el-divider{
    margin:0 auto;
    width: 40%;
  }
  .el-card{
    width: 70%;
    margin-left: 15%;
    margin-top: 50px;
    height: auto;
  }
#image{
  height: auto;
}
.button{
color:rgb(51, 49, 49);
  border-width: 0;
  font-size: 1em;
 background-color: rgba(0,0, 0, 0);
}
 :focus{
  outline: none;
}
.block223{
  /* background-color: aquamarine; */
  margin-top: 50px;
 margin-left: 25%; 
 width: 50%;


 
}

</style>





<script> 
export default {
  
  data () {
    return {
      msg: '投资哲学',
      msg1: 'INVESTMENT',
      currentDate: new Date(),
      list:[],
      queryInfo: {
        title: '',
        type: '',
        pagenum: 1,
        pagesize: 6,
      },
      
      imgsrc:'http://101.37.116.37:5000/public/files/images/3-',
      switchName: [
        {
          cut: false
        },
        {
          cut: false
        },
        {
          cut: false
        },
        {
          cut: false
        },
        {
          cut: false
        }
      ]


   

    }
  }, 
  created () {
    this.test()
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
 

  toggleShopShow (index) {
        this.switchName[index].cut = !this.switchName[index].cut;

      },
  




  }
 
}
</script>

<style>
  .time {
    font-size: 13px;
    color: #999;
  }
  
  .el-row{
    margin: 0 auto;
    margin-top: 3%;
    width: 80%;
    margin-bottom: 20px;
  }

  #control-left1{
      padding-left: 3%;
  }

  .image{
      width: 100%;
      position: relative;
      margin-bottom: 10%;
  }
 .el-col{
     margin-top: 10px;
 }


  /* .image {
    width: 50%;
    display: inline-block;
    float: left;
  }

  #text1{
      display: inline-block;
      float: right;
  }
  .bottom {
    margin-top: 13px;
    line-height: 12px;
  } */

  /* .clearfix:before,
  .clearfix:after {
      display: table;
      content: "";
  }
  
  .clearfix:after {
      clear: both
  } */
</style>