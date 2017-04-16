<template>
  <div id="app">
    <div class="Application">
        <header class="Application--header">
          <h1>Lunch Rush</h1>
        </header>
        <div>
          <sign-in v-if='!isLoggedIn'></sign-in>
          <current-user 
            :user="currentUser"
            v-if='isLoggedIn'
          ></current-user>
        </div>
      </div>
  </div>
</template>

<script>
import { auth } from './firebase';
import CurrentUser from './components/CurrentUser';
import SignIn from './components/SignIn';

export default {
  name: 'app',
  data() {
    return {
      currentUser: null,
    };
  },
  computed: {
    isLoggedIn() {
      return this.currentUser && Object.keys(this.currentUser).length;
    },
  },
  components: {
    'current-user': CurrentUser,
    'sign-in': SignIn,
  },
  created() {
    auth.onAuthStateChanged((currentUser) => {
      this.currentUser = Object.assign({}, currentUser);
    });
  },
};
</script>

<style>
.Application {
  margin: auto;
  width: 800px;
}

</style>
