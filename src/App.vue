<template>
  <div id="app">
    <div id="nav">
      <!-- This part lets you swich between the pages -->
      <router-link to="/">Home</router-link> |
      <router-link to="/leaderboard">LeaderBoard</router-link> |
      <router-link to="/stats">Stats</router-link>
    </div>
    <router-view />
  </div>
</template>

     
<style>
 <!-- changes how the app looks -->
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
