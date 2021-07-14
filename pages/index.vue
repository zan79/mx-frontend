<template>
  <div>
    <NavBar />
    <div class="container mt-5">
      <h1 class="text-center pt-5">
        <span class="text-success">Welcome</span>
        <span class="text-primary">to</span>
        <span class="text-info">the</span>
        <span class="text-warning">page</span>
        </h1>

      <h3 class="text-light text-center mt-5" v-if="$auth.loggedIn">
      {{$auth.user.name}}
      </h3>

      <h2 class="text-secondary text-center mt-5">
        Have a nice day
        <span class="text-danger"> =)</span>
      </h2>
    </div>
    
  </div>
</template>

<script>
export default {
  auth: false
}
</script>

<style>
body{
  background-color: #212121;
}
</style>