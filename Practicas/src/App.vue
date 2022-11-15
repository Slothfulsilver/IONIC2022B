<template>
  <ion-app>
    <ion-router-outlet />
  </ion-app>
</template>

<script>
import { IonApp, IonRouterOutlet } from '@ionic/vue';
import { defineComponent } from 'vue';
import {getAuth, signInWithEmailAndPassword} from 'firebase/auth'
export default defineComponent({
  name: 'App',
  components: {
    IonApp,
    IonRouterOutlet
  }, 
  created(){
    const auth = getAuth()
    signInWithEmailAndPassword(auth, "arturo@a.com", "Tulos12345").then((userCredential) => {
      const user = userCredential.user

      if (user == null){
        console.log("Not authentified")
      }
      else {
        console.log("User Authentified", user)
      }
    })

  }
});
</script>