<template>
  <div class="CurrentUser">
    <img
      :src='user.photoURL'
      class="CurrentUser--photo"
    />
    <div class="CurrentUser--identification">
      <button @click='signOut'>
        Sign Out
      </button>
    </div>
  </div>
</template>
<script>
  import { auth } from '../firebase';

  export default {
    name: 'currentuser',
    methods: {
      signOut() {
        auth.signOut();
      },
    },
    props: [
      'user',
    ],
  };
</script>
