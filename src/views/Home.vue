<template>
  <main>
    <div v-bind:key="collection.id" v-for="collection in collections">
      <div class="collection-container">
        <span @click="gotoTopic(collection.name)">
          {{ collection.name }}
        </span>
      </div>
    </div>
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
        const res = await fetch(`http://localhost:5910/cheatsheets`);
        const json = await res.json();
        // console.log(json);
        return json;
      } catch (e) {
        console.log(e);
      }
    },
    gotoTopic(collection) {
      const path = `/category/${collection}`;
      // console.log(path);
      this.$router.push({
        path: path,
      });
    },
  },
  async created() {
    this.collections = await this.fetchTopics();
  },
};
</script>

<style scoped>


main .collection-container h2 {
  text-transform: capitalize;
}

.collection-container {
  cursor: pointer;
  width: 200px;
  margin: 0em auto;
  padding: 1em 0em;
}

.collection-container span {
  padding: .5em;
  background-color: rgb(88, 152, 236);
  border-radius: 15px;
}
</style>