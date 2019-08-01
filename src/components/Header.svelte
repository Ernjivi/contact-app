<script>
import { auth, googleProvider } from '../firebase';

import { user } from '../stores';


let userData;
const unsubcribe = user.subscribe(value => userData = value);
</script>

<style>
  header {
    background: black;
    color: white;
  }
</style>

<header>
  <h1>Contacts</h1>
  {#if userData.displayName}
    <p>
      <img src="{userData.photoURL}" width="100" alt="User avatar">
      {userData.displayName}
    </p>
    <button on:click={ () => auth.signOut() }>Logout</button>
  {:else}
    <button on:click={ () => auth.signInWithPopup(googleProvider) }>Login</button>
  {/if}
</header>