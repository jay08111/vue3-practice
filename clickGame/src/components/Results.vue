<template>
  <p>Reaction Time : {{ score }}ms</p>
  <p>{{ rank }}</p>
</template>
<script>
export default {
  props: {
    score: {
      type: null,
    },
  },
  data() {
    return {
      rank: null,
    };
  },
  methods: {},
  mounted() {
    if (this.score < 250) {
      this.rank = "God";
    } else if (this.score < 400) {
      this.rank = "Rappid reflexes";
    } else {
      this.rank = "snail pace ...";
    }
  },
};
</script>
<style scoped></style>
