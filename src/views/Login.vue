<template>
  <div class="login">
    <form v-if="login" @submit.prevent="loginUser">
      <input type="email" v-model="creds.email" placeholder="email">
      <input type="password" v-model="creds.password" placeholder="password">
      <button type="submit">Login</button>
    </form>
    <form v-else @submit.prevent="register">
      <input type="text" v-model="newUser.name" placeholder="name">
      <input type="email" v-model="newUser.email" placeholder="email">
      <input type="password" v-model="newUser.password" placeholder="password">
      <button type="submit">Create Account</button>
    </form>
    <div @click="login = !login">
      <p v-if="login">No account Click to Register</p>
      <p v-else>Already have an account click to Login</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "login",
  mounted() {
    this.$store.dispatch("authenticate");
  },
  data() {
    return {
      login: true,
      creds: {
        email: "",
        password: ""
      },
      newUser: {
        email: "",
        password: "",
        name: ""
      }
    };
  },
  methods: {
    register() {
      this.$store.dispatch("register", this.newUser);
    },
    loginUser() {
      this.$store.dispatch("login", this.creds);
    }
  }
};
</script>