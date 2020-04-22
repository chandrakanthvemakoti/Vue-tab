<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <h1>Form</h1>
                    <hr>
                   
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input
                                type="text"
                                id="name"
                                class="form-control"
                                v-model="name"
                               >
                    </div>
                      
                      <div class="form-group">
                        <label for="email">Email</label>
                        <input
                                type="email"
                                id="email"
                                class="form-control"
                                v-model="email"
                                >
                    </div>
                          
                      <div class="form-group">
                        <label for="role">role</label>
                        <input
                                type="text"
                                id="role"
                                class="form-control"
                                v-model="role"
                                >
                    </div>     

                    </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <button
                            class="btn btn-primary"
                            @click="addnew"
                            >Submit
                    </button>
                </div>
            </div>
            
                    </form>
<br>
<br>
 

 <div>
    <app-table :items="employee" :columns="headers" ></app-table>
    </div>
                   


    </div>

   
</template>
<script>
import Table from './Table.vue'
export default {
   data(){
       return{
      
     headers: [ 'name', 'email', 'role'],
      name:'',
      email:'',
      role:'',
      employee:[]
    
       }

   },


   methods:{
       addnew: function(){
           var my_object ={
              
               name: this.name,
               email:this.email,
               role:this.role
           };
           this.employee.push(my_object)
           
           this.name='';
           this.email='';
           this.role='';

    //      this.users.push({name:this.newElement.name,email:this.newElement.email,role:this.newElement.role});
    //   this.newElement = {name:"",email:"",role:""};
       }
   },

   components:{
       appTable: Table
   }
   
}
</script>