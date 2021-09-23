<template>
  <nav>
    <ul>
      <li><router-link to="/">Home</router-link></li>
      <li><router-link to="/category/blender">Blender</router-link></li>
      <li><router-link to="/about">About</router-link></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Nav",
};
</script>

<style>
  nav {
    font-weight: bold;
  }

  nav li {
    list-style: none;
  }

  nav a {
    text-decoration: none;
    color: black;
  }

  @media screen and  (min-width: 480px) {
    nav {
      position: relative;
      height: var(--nav-height);
    }
    nav ul {
      display: flex;
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      /* align-items: center; */
      /* padding: .5em 1em; */
    }

    nav a {
      padding: 0em 1em;
    }
  }
</style>