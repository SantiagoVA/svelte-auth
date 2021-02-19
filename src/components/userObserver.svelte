<script>
    import {onMount} from 'svelte';
    import {currentUser} from "../stores/user.js";
    onMount(() => {
    firebase.auth().onAuthStateChanged((user) => {
    if (user) {
      var displayName = user.displayName;
      var email = user.email;
      var emailVerified = user.emailVerified;
      var photoURL = user.photoURL;
      var isAnonymous = user.isAnonymous;
      var uid = user.uid;
      var providerData = user.providerData;
      console.log('user',user)
      console.log(providerData)
      currentUser.set(user)
        // ...
    } else {
        // User is signed out
        // ...
        currentUser.set(null)
        console.log('User is not signed out')
    }
    });
    });
    
</script>