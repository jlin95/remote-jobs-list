  
<style>
.class {
  /* font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif; */
  font-size: 32px;
  color: black;
}
a:link {
  text-decoration: none;
  color: grey;
}
a:hover {
  text-decoration: underline;
  color: black;
}
a:visited {
  color: grey;
}
</style>

<template>
  <div id="app">
    <h1>Remote OK Jobs Board</h1>
    <div v-for="job in jobs" class="job" v-bind:key="job">
      <a v-bind:href="job.url">{{ job.position }}</a>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "app",
  data() {
    return {
      jobs: null
    };
  },
  mounted() {
    axios.get("https://remoteok.io/api").then(response => {
      response.data.shift();
      this.jobs = response.data;
      return this.jobs;
    });
  }
};
</script>
