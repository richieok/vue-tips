<template>
  <Nav/>
  <main>
    <router-view/>
  </main>
  <Footer/>
</template>

<script>
import Nav from "@/components/Nav.vue";
import Footer from "@/components/Footer.vue";
export default {
  components: {
    Nav,
    Footer
  }
}
</script>

<style>
:root {
  --nav-height: 2.5em;
}

* {

  padding: 0;
  margin: 0;
  box-sizing: border-box;
  color: #2c3e50;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
}

body {
  background-color: rgb(159, 202, 226);

}

/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
} */

main {
  min-height: calc(100vh - var(--nav-height));
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
