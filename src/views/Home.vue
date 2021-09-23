<template>
  <main>
    <ul>
      <li v-bind:key="collection.id" v-for="collection in collections">
        <div class="collection-container">
          <h1><span class="collection" @click="gotoTopic(collection.name)">{{ collection.name }}</span></h1>
        </div>
      </li>
    </ul>
  </main>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  data() {
    return {
      collections: [],
    };
  },
  methods: {
    async fetchTopics() {
      try {
        const res = await fetch("http://localhost:5000/cheatsheets");
        const json = await res.json();
        // console.log(json);
        return json;
      } catch (e) {
        console.log(e);
      }
    },
    gotoTopic(collection){
      const path = `/category/${collection}`;
      // console.log(path);
      this.$router.push({
        path: path
      });
    }
  },
  async created() {
    this.collections = await this.fetchTopics();
  }
};
</script>

<style>
main ul li h1 {
  text-transform: capitalize;
}
.collection {
  margin: .5em 1em;
  cursor: pointer;
  background-color: darkgray;
}
.collection-container {
  margin: .5em 1em;
}
</style>