<template>
  <div class="tip-card">
    <h2>{{ this.tip.topicName }}</h2>
    <ul :key="shortcut.command" v-for="shortcut in this.tip.shortcuts">
        <li>{{shortcut.command}}: {{shortcut.description}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TipCard",
  props: {
    tip: Object,
  },
};
</script>

<style scoped>
  .tip-card {
    border: dotted 2px black;
  }

  ul {
    list-style: none;
  }
</style>