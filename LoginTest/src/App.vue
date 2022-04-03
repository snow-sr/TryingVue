<template>
  <main>

    <Login v-if='!user.logged'/>
    
  </main>
</template>

<script>

import Login from "./components/login.vue";

export default {

  components: { Login },
  
  name: "LoginTest",

  data() {
    return {
      message: "Hello Vue!",
      user: {
        logged: false
      }
    };
  },
};
</script>
