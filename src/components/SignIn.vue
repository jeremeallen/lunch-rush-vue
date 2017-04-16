<template>
  <div class="SignIn">
    <button @click="signIn">
      Sign In
    </button>
  </div>
</template>
<script>
  import { auth, googleAuthProvider } from '../firebase';

  export default {
    name: 'signin',
    methods: {
      signIn() {
        auth.signInWithPopup(googleAuthProvider);
      },
    },
  };
</script>
