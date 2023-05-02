<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link :to="{ name: 'AboutView'}">About</router-link> |  <!-- better way to avoid pass the path here cause you may change it in future in router file and you have to reflect it here, but with the name no need -->
    <router-link :to="{name: 'JobsView'}">Jobs</router-link>
  </nav>

  <button @click="redirect">Redirect</button>
  <button @click="back">Go Back</button>
  <button @click="forward">Go Forwrd</button>
  <router-view/>
</template>

<script>
export default {
  methods: {
    redirect() {
      this.$router.push({name: 'AboutView'})
    },
    back() {
      this.$router.go(-1) // or -2... it depends what the number of steps you want back
    },
    forward() {
      this.$router.go(1) // or 2,3... //
    }
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  padding: 10px;
  border-radius: 4px;
}

nav a.router-link-exact-active {
  color: white;
  background: crimson;
}
button {
  margin: 0 10px;
  padding: 10px;
  border: none;
  border-radius: 4px;
}
</style>
