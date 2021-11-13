<template>
 <div >
  
  <Stock></Stock>
    <Report></Report>
     
       <Investigation></Investigation> 
       <Investment></Investment>
       <Other></Other>

 </div>
</template>

<script>

import Stock from '../components/stock.vue'
import Report from '../components/report.vue'
import Investment from '../components/investment.vue'

import Investigation from '../components/Investigation.vue'
import Other from '../components/other.vue'


export default {
 components:{

Stock,
Report,
 Investment,
  Investigation,
   Other

  
 
 }
}
</script>