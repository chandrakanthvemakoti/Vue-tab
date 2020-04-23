<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <h1>Form</h1>
                    <hr>
                   
                    <div class="form-group" :class="{invalid: $v.name.$error}">
                        <label for="name">Name</label>
                        <input
                                type="text"
                                id="name"
                                class="form-control"
                                v-model="name"
                                
                                @blur="$v.name.$touch()"
                               >
                    </div>
                    <p v-if="!$v.name.required" style="color:red">*please enter the name</p>
                      
                      <div class="form-group" :class="{invalid: $v.email.$error}">
                        <label for="email">Email</label>
                        <input
                                type="email"
                                id="email"
                                class="form-control"
                                v-model="email"
                                @blur="$v.email.$touch()"
                                >
                    </div>
                    <p v-if="!$v.email.email"  style="color:red">*please enter the valid email</p>
                        <p v-if="!$v.email.required" style="color:red">*please enter the email</p>   
                      <div class="form-group" :class="{invalid: $v.role.$error}">
                        <label for="role">role</label>
                       <select 
                        id="role"
                        class="form-control"
                        v-model="role"
                         @blur="$v.role.$touch()">
                          <option value="" disabled selected hidden>Please Select</option>

                  <option v-for="ro in roles">{{ro}}</option>
                       </select>
                    </div>  
                     <p v-if="!$v.role.required" style="color:red">*please select the role</p>   

                    </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <button
                            class="btn btn-primary"
                            @click="addnew"
                            :disabled="$v.$invalid"

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
import {required,email} from 'vuelidate/lib/validators'
import Table from './Table.vue'

export default {
   data(){
       return{
      
     headers: [ 'name', 'email', 'role'],
      name:'',
      email:'',
      roles: [' js developer','vue developer','node developer'],
      role:'',
      employee:[]
    
       }

   },


   methods:{
       addnew: function(e){
           e.preventDefault();
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
   },
   validations:{
       name:{
           required
       },
       email:{
           required,
           email
       },
       role:{
           required
       }
   }
   
}
</script>