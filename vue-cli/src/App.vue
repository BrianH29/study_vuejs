<template>
  <div>
    <app-header></app-header>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'

//basic vue component 입력 방식 
// var AppHeader = {
//   template: '<header><h1>Header</h1></header>'
// }

//basic vue instance 입력 방식 
// new Vue({
//   data:{
//     str: 'hi'
//   }
// });

export default {
  data:function(){
    return {
      str: 'hi'
    }
  },
  components: {
    'app-header': AppHeader
  }
}
</script>

<style>

</style>