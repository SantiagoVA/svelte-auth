<script>
    import {currentUser} from "../stores/user.js"
    import {onMount} from 'svelte'
    onMount(() => {
        createLoginButton();
    });
    function signOut(){
        firebase.auth().signOut().then(function() {
        console.log('logout');
        location.reload();
        }).catch(function(error){
        alert(error)
        })
    }
    function createLoginButton(){    
      // FirebaseUI config.
      var uiConfig = {
        signInOptions: [
          // Leave the lines as is for the providers you want to offer your users.
          firebase.auth.GoogleAuthProvider.PROVIDER_ID
        ],
        callbacks: {
            signInSuccessWithAuthResult: function(authResult, redirectUrl){
                return false;
            }
        }
        // tosUrl and privacyPolicyUrl accept either url string or a callback
        // function.
        // Terms of service url/callback.
      };

      // Initialize the FirebaseUI Widget using Firebase.
      var ui = firebaseui.auth.AuthUI.getInstance() || new firebaseui.auth.AuthUI(firebase.auth());
      // The start method will wait until the DOM is loaded.
      ui.start('#firebaseui-auth-container', uiConfig);
    
    };
</script>
{#if $currentUser}
<div class="button-container">
<button on:click={() => {signOut()}}>Logout</button> 
</div>
{/if}
{#if !$currentUser}
<div class="logout" id="firebaseui-auth-container">
</div>
{/if}

<style>
  
  .button-container{
    display: flex;
    justify-content: center;
    position: relative;
    top: 20px;
  }

  button{
    width: 100px;
    height: 30px;
    border: none;
    border-radius: 10px;
    font-family: Roboto, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
    font-weight: bold;
    background-color: #49bcdc;
    background-image: linear-gradient(315deg, #49bcdc 0%, #d3d3d3 74%);
    transition: all 0.25s ease;
  }

  button:hover{
    border-radius: 15px;
  }

</style>
