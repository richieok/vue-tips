<template>
  <div>
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