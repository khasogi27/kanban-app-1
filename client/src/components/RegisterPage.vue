<template>
  <section class="container" id="register">
    <div class="row justify-content-center mt-5 text-white">
      <div class="col-4 fas">
        <h1 class="text-white">Register</h1>
        <form @submit.prevent="register">
          <div class="form-group">
            <label form="name">Email</label>
            <input
              v-model="email"
              type="email"
              id="req-email"
              class="form-control"
              placeholder="input your email"
              autocomplete="email"
            />
          </div>
          <div class="form-group">
            <label form="password">Password</label>
            <input
              v-model="password"
              type="password"
              id="req-password"
              class="form-control"
              placeholder="input your password"
              autocomplete="current-password"
            />
          </div>
          <button type="submit" class="btn btn-success">Register</button>
          <button @click.prevent="toLogin" class="btn btn-primary">Login</button>
          <div class="justify-content-center"></div>
        </form>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "RegisterPage",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    register() {
      let paylod = {
        email: this.email,
        password: this.password,
      };
      this.$emit("register", paylod);
    },

    toLogin() {
      this.$emit('changePage', 'login-page')
    }
  },
};
</script>

<style>
</style>