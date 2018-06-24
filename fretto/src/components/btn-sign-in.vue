<template>
 <div ref="signinBtn">
   <q-btn  
           class = "sign-in-btn"
           color = "secondary" 
           @click="signIn"
           :params="googleSignInParams"
           @success="onSignInSuccess"
           @error="onSignInError"> Sign-in</q-btn>
</div>           

</template>

<script>


  export default {
    props: ['value', 'options'],
    data(){
        return{
             googleSignInParams: {
                client_id: '727605426258-fh3lfku2tmo2d5e50oc6t7lsrbk1iths.apps.googleusercontent.com'
             },
            GoogleAuth: ''
        }
    },
      mounted () {
    window.gapi.load('auth2', () => {
      const auth2 = window.gapi.auth2.init({
        client_id: '727605426258-fh3lfku2tmo2d5e50oc6t7lsrbk1iths.apps.googleusercontent.com',
        cookiepolicy: 'single_host_origin'
      })
         this.GoogleAuth = gapi.auth2.getAuthInstance();
      auth2.attachClickHandler(this.$refs.signinBtn, {}, googleUser => {
        this.$emit('done', googleUser)
      }, error => console.log("mounted " + error))
    })
   
  },
    methods: {
     
        onSignInSuccess (googleUser) {
        // `googleUser` is the GoogleUser object that represents the just-signed-in user.
        // See https://developers.google.com/identity/sign-in/web/reference#users
            const profile = googleUser.getBasicProfile() // etc etc
            console.log(profile.getBasicProfile())
        },
        onSignInError (error) {
        // `error` contains any error occurred.
         console.log('OH NOES', error)
         console.log("error in sign-in")
        },
        signIn(){
            console.log("sign-in clicked");
            console.log( this.GoogleAuth.currentUser.get() )
        }

    }
  }
</script>

<style>
   .sign-in-btn {
      display: flex;
      height: 105px;
      width: 350px;
      font-size: 50px;
  }
</style>
