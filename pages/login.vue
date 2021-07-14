<template>
  <div>
    <NavBar />

    <div class="container">
      <div class="row">
        <div class="col-md-4 offset-md-4 mt-5">
          <b-card header="User Login" bg-variant="dark" text-variant="primary" border-variant="primary">
            <form action="#" @submit.prevent="onLogin()">
              <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" v-model="credentials.email" class="form-control" />
              </div>
              <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" v-model="credentials.password" class="form-control" />
              </div>
              <div class="form-group">
                <button class="btn btn-primary btn-block mt-4" type="submit">Login</button>
              </div>
            </form>
          </b-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      credentials: {}
    }
  },
  methods: {
    async onLogin() {
      await this.$auth.loginWith('local', {data: this.credentials})
      .then(()=>{
        //auth saves the day
      })
      .catch((err)=>{
        alert("Invalid Credentials")
      })
    }
  }
}
</script>

<style>
body{
  background-color: #212121;
}
</style>