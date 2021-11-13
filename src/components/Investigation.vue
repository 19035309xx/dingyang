<template>
<div>
  <el-row>
    <h2 style="text-align:center">{{msg}}</h2>
    <p style="text-align:center">{{msg1}}</p>
    <el-divider></el-divider>
      <el-col :span="12">
          <div class="grid-content bg-purple">
              <el-collapse v-model="activeNames" @change="handleChange">
                  <el-collapse-item v-for="item in articlelist" :key="item.id" :title="item.title" :name="item.id">
                      <div>{{item.content}}</div>
                  </el-collapse-item>

              </el-collapse>
          </div>
      </el-col>
      <el-col :span="12">
          <div class="grid-content bg-purple-light">
              <el-collapse v-model="activeNames" @change="handleChange">
                  <el-collapse-item v-for="item in articlelist2" :key="item.id" :title="item.title" :name="item.id">
                      <div>{{item.content}}</div>
                  </el-collapse-item>
              </el-collapse>
          </div>
      </el-col>
  </el-row>
</div>
</template>


<script>

export default {
 
  data() {
      return {
        msg: '其他文章',
      msg1: 'INVESTIGATION',
        activeNames: ['1'],
        articlelist:[],
        articlelist2:[]
      };
    },
    created(){
      this.getarticlelist()
    },
    methods: {
      handleChange(val) {
        console.log(val);
      },
      async getarticlelist(){
        const res =await this.$http.get('/huayin/get-articles',{
          params:{
            title:'',
            type:'',
            pagenum:'5',
            pagesize:'4'
          }
          
          
        })
        const res2 =await this.$http.get('/huayin/get-articles',{
          params:{
            title:'',
            type:'',
            pagenum:'6',
            pagesize:'4'
          }
        })
        this.articlelist=res.data.data
        this.articlelist2=res2.data.data


      }
    }
  }
</script>

<style>
  .el-row {
    margin: 0 auto;
    margin-top: 1%;
    width: 80%;
    margin-bottom: 20px;
    /* &:last-child {
      margin-bottom: 0;
    } */
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
</style>