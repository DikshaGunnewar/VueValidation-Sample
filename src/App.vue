<template>
  <div id="app">
    <h1 class="title">Form</h1>
    <form @submit.prevent="validateBeforeSubmit">

    <div class="column is-6">
        <label class="label">Organization Name</label>
        <div class="control has-icon has-icon-right">
            <input  name="organizationname" v-model="organizationname" v-validate="'required|alpha'" :class="{'input': true, 'is-danger': errors.has('organizationname') }" type="text" placeholder="Organization Name">   
             <span class="icon is-small is-right">
                  <i v-show="errors.has('organizationname')" class="fa fa-warning"></i>
             </span>          
            <span v-show="errors.has('organizationname')" class="help is-danger">{{ errors.first('organizationname') }}</span>
        </div>
    </div>
    <div class="column is-6 ">
        <label class="label">Email</label>
        <div class="control has-icon has-icon-right">
            <input name="email" v-model="email" v-validate="'required|email'" :class="{'input': true, 'is-danger': errors.has('email') }" type="text" placeholder="Email">
              <span class="icon is-small is-right">
                 <i v-show="errors.has('email')" class="fa fa-warning"></i>
              </span>
            <span v-show="errors.has('email')" class="help is-danger">{{ errors.first('email') }}</span>
        </div>
    </div>
    
    <div class="column is-6">
        <label class="label">Password</label>
        <div class="control has-icon has-icon-right">
            <input name="password" v-model="password" v-validate="'required'" :class="{'input': true, 'is-danger': errors.has('password') }" type="password" placeholder="Password">
             <span class="icon is-small is-right">
                <i v-show="errors.has('password')" class="fa fa-warning"></i>
             </span>
             <span v-show="errors.has('password')" class="help is-danger">{{ errors.first('password') }}</span>
        </div>
    </div>
    <div class="column is-6">
        <label class="label">Confirm Password</label>
        <div class="control has-icon has-icon-right">
            <input name="confirmpassword" v-model="confirmpassword" v-validate="'required|confirmed:password'" :class="{'input': true, 'is-danger': errors.has('confirmpassword') }" type="password" placeholder="Confirm Password">
              <span class="icon is-small is-right">
                <i v-show="errors.has('confirmpassword')" class="fa fa-warning"></i>
              </span>
              <span v-show="errors.has('confirmpassword')" class="help is-danger">{{ errors.first('confirmpassword') }}</span>
        </div>
    </div>

    <div class="column is-6">
        <p class="control">
            <button class="button is-primary" type="submit">Submit</button>
           
        </p>
    </div>
</form>
    
  </div>
</template>
<script>
export default {
  name: 'form-example',
  data: () => ({
    organizationname: '',
    email: '',   
    password: '',
    confirmpassword: '',
   
  }),
  methods: {
    validateBeforeSubmit() {
      this.$validator.validateAll().then((result) => {
        if (result) {
          // eslint-disable-next-line
          alert('From Submitted!');
          return;
        }

        alert('something went wrong!');
         
      });
    }
  }
};
</script>


<style>

#app{
    margin-left:500px;
}

</style>
