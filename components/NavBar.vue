<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="dark">
      <b-navbar-brand href="/" class="ml-5"><h3>MX Project</h3></b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="ml-auto mr-5">
          <template v-if="$auth.loggedIn">
            <b-nav-item href="/dashboard"><span class=" btn btn-info">Dashboard</span></b-nav-item>
            <b-nav-item href="/products"><span class=" btn btn-warning">Products</span></b-nav-item>
            <b-nav-item href="#" @click.prevent="onLogout"><span class=" btn btn-danger">Logout</span></b-nav-item>
          </template>
          <template v-else>
            <b-nav-item href="/register"><span class=" btn btn-success">Register</span></b-nav-item>
            <b-nav-item href="/login"><span class=" btn btn-primary">Login</span></b-nav-item>
          </template>  
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  methods: {
    async onLogout() {
      await this.$auth.logout()
    }
  }
}
</script>

<style>
</style>