<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>The job id is {{ id }}</p>
    <p>{{ job.details }}</p>
  </div>
  <div v-else>
    <h2>Loading...</h2>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: Number || String,
    },
  },
  data() {
    return {
      job: null,
    };
  },
  mounted() {
    fetch("http://localhost:3001/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
h2 {
  text-align: center;
  font-size: 2rem;
}
</style>
