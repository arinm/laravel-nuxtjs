<template>
  <section class="section">
    <div class="container">
      <div class="columns is-centered">
        <div class="column is-one-third">
          <h2 class="title has-text-centered">Login</h2>

          <form method="post" @submit.prevent="login">
    
              <input
                type="email"
                v-model="email"
                required />
            

           
              <input
                type="password"
                v-model="password"
                password-reveal
                required>
                />
          

            <button type="is-dark is-fullwidth" native-type="submit">
              Login
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    async login() {
      await this.$auth.loginWith('laravelSanctum', {
        data: {
          email: this.email,
          password: this.password,
        },
      })

     this.$router.push('/')
    },
  },
}
</script>