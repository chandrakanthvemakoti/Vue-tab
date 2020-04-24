<template>
    <div class="container">
   <h1>MY DASHBOARD</h1>
   <hr>
    <div class="col-sm-12">
    <app-table :items="contents" :columns="headers"  ></app-table>
    </div>
    <div class="col-sm-12">
    <app-formtable @myemit="contents=$event"></app-formtable>
    </div>
    
   </div>
   </template>
    <script>
     import Formtable from './Formtable.vue';
      import Table from './Table.vue';
      export default{
     data(){
  return{

    headers: [  'name', 'email', 'role'],

    contents: [
    {
          
          
          'name':'',
          'email':'',
          'role':''
    }
    
    ]
    
  }
 },
          components:{
            appTable: Table,
            appFormtable:Formtable
          },
   
      }
    </script>
<style scoped>
div{
    text-align: center;
}
</style>