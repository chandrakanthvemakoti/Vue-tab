<template>
    <div class="dash">
   <h1>MY DASHBOARD</h1>
   <hr>
   <div class="container">
    <app-formtable></app-formtable>
    <div>
   
    </div>
    
   </div>
   </div>
   </template>
    <script>
  
      
      import Formtable from './Formtable.vue'
      export default{
     data(){
  return{

    
  }
 },
  
          components:{
            
            appFormtable:Formtable
          },
   
      }
    </script>
<style scoped>
.dash{
    text-align: center;
}
</style>