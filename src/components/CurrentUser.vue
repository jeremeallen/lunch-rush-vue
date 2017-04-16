<template>
  <div class="CurrentUser">
    <img
      :src='user.photoURL'
      class="CurrentUser--photo"
    />
    <div class="CurrentUser--identification">
      <h3>{{ user.displayName }}</h3>
      <p>{{ user.email }}</p>    
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
<style>
.CurrentUser {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
}

.CurrentUser--identification {
  padding: 1em;
  flex: 1;
}

.CurrentUser--photo {
  max-height: 150px;
}
</style>
