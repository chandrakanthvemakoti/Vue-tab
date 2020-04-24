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
                                @blur="$v.name.$touch()"
                                v-model="name"
                               >
                    </div>
                    <p v-if="!$v.name.required" style="color:red">*please enter your name</p>
                      
                      <div class="form-group" :class="{invalid: $v.email.$error}">
                        <label for="email">Email</label>
                        <input
                                type="email"
                                id="email"
                                class="form-control"
                                 @blur="$v.email.$touch()"
                                v-model="email"
                                >
                    </div>
                         <p v-if="!$v.email.required" style="color:red">*please enter the mail id</p> 
                         <p v-if="!$v.email.email" style="color:red">*please enter valid mail id</p>
                      <div class="form-group" :class="{invalid: $v.role.$error}">
                        <label for="role">role</label>
                        <select
                                
                                id="role"
                                class="form-control"
                                v-model="role"
                                @blur="$v.role.$touch()"
                                >
                                
                          <option value="" disabled selected hidden>Please Select</option>
                            <option v-for="ro in roles">{{ro}}</option>

                                </select>
                    </div>  
                    <p v-if="!$v.role.required" style="color:red">*please select your role</p>   

                    </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <button
                            class="btn btn-primary"
                            :disabled="$v.$invalid"
                            @click="addnew">Submit
                    </button>
                </div>
            </div>
            
                    </form>
<br>
<br>
 

                   


    </div>

   
</template>
<script>
import {required,email} from "vuelidate/lib/validators"
export default {
   data(){
       return{
     
    
      name:'',
      email:'',
      roles: [' react developer','vue developer','node developer'],
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
        
           this.employee.push(my_object);
           
          this.$emit('myemit',this.employee);
             this.name='';
             this.email='';
             this.role='';
         }
       
       
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