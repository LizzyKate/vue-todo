<template>
 <div id="app" class="container">
   <todo></todo>
 </div>
</template>

<script>

import todo from './components/todo'

export default {
  components:{
    todo:todo
  },
  data(){
    return{
     
    }
  }
}
</script>

<style>
*{
  box-sizing:border-box;
}
.container{
  max-width: 600px;
   margin: 0 auto;
}
#app{
  color: #2c3e50;
  margin-top: 60px;
}
</style>
