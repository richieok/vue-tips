<template>
  <div class="container">
    <div v-bind:key="category._id" v-for="category in categories">
      <TipCard :tip="category" />
    </div>
  </div>
</template>

<script>
import TipCard from "@/components/TipCard";
export default {
  name: "Category",
  components: {
    TipCard,
  },
  data() {
    return {
      categories: [],
    };
  },
  methods: {
    async fetchTopics(category) {
      try {
        const res = await fetch(
          `http://localhost:5910/cheatsheets/${category}`
        );
        const json = await res.json();
        // console.log(json);
        return json;
      } catch (e) {
        console.log(e);
      }
    },
  },
  async created() {
    this.categories = await this.fetchTopics(this.$route.params.category);
    // console.log(this.$route.params);
  },
};
</script>

<style scoped>
.container {
  display: block;
}

@media screen and (min-width: 480px) {
}
.container {
  display: flex;
}
</style>