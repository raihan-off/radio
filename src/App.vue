<template>
  <div id="app">
    <div id="nav">
      <router-link class="rout" to="/">Home</router-link>
      <router-link class="rout" to="/favorite">Favorite</router-link>
      <router-link class="rout" to="/about">About</router-link>
    </div>
    <router-view />
  </div>
</template>

<style>
* {
  padding: 0%;
  margin: 0%;
  background-color: #7e0cf5;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  text-align: end;
  padding: 40px 30px 60px 0px;
}

#nav a {
  font-weight: bold;
  color: white;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  /* color: #42b983; */
  color: black;
  text-decoration: none;
}

.rout {
  margin: 10px;
}
</style>
