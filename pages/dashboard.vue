<template>
  <div>
    <NavBar />
    
    <div class="container mt-5">
      <h1 class="text-info">Dashboard</h1>
      <table class="table table-striped table-dark">
        <thead>
          <th class="bg-info text-center">&nbsp;</th>
          <th class="bg-info text-center">&nbsp;</th>
        </thead>
        <tbody>
          <tr><th>ID</th><td>{{$auth.user.id}}</td></tr>
          <tr><th>User</th><td>{{$auth.user.name}}</td></tr>
          <tr><th>Email</th><td>{{$auth.user.email}}</td></tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>
body{
  background-color: #212121;
}
</style>