<template>
  <div>
    <nav>
      <router-link to="/">Login</router-link> |
      <router-link to="">Todos</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #4e0c6e;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #686868;
}

nav a.router-link-exact-active {
  color: #5d1b7d;
}
</style>
