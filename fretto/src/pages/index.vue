<template>
  <q-page class="flex flex-center">
     <!-- <div>
        <q-btn v-show= "1" class = "s-btn" color = "secondary" @click="signIn"> Sign-in</q-btn>
        <q-btn v-show= "isSignedIn" class = "s-btn" color = "secondary"> Sign-out</q-btn>
     </div> -->
        <btn-sign-in> Google Sign-in </btn-sign-in>
  </q-page>

</template>

<script>
import Vue from 'vue'
import BtnSignIn from 'components/btn-sign-in.vue'

export default {
  name: 'PageIndex',
  components:{
      BtnSignIn
  },
  data(){
     return{
         isSignedIn: false
        
     }
  },
  methods: {
       signIn: function(){
          console.log()
       },
      
  }
}
</script>

<style scoped>

 

  .g-signin-button {
       /* This is where you control how the button looks. Be creative! */
       display: inline-flex;
  position: relative;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
  min-width: 200px;
  height: $mdc-button-height;
  border: 2px;
  border-color: red;

}
</style>
