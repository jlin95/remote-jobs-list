  
<style>
.class {
  /* font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif; */
  font-size: 32px;
  color: black;
}
a:link {
  text-decoration: none;
  color: black;
}
a:hover {
  text-decoration: underline;
  color: black;
}
a:visited {
  color: grey;
}
.job-item {
  border-radius: 4px;
  width: 300px;
  padding: 8px 10px;
  margin: 0 auto 16px;
  -webkit-box-shadow: 10px 10px 16px 0px rgba(99, 131, 131, 0.16);
  -moz-box-shadow: 10px 10px 16px 0px rgba(99, 131, 131, 0.16);
  box-shadow: 10px 10px 16px 0px rgba(99, 131, 131, 0.16);
}

.job-item > div > img {
  border-radius: 10px;
  width: 100px;
  height: 100%;
  object-fit: cover;
}

.company {
  font-size: 15px;
  color: #638383;
  font-weight: bold;
  margin: 0;
}

.position {
  color: black;
}
</style>

<template>
  <div id="app">
    <h1>Remote OK Jobs Board</h1>
    <div v-for="job in jobs" class="job" v-bind:key="job.id">
      <div key="job.id" class="job-item">
        <p class="company">{{ job.company }}</p>
        <a class="position" v-bind:href="job.url">{{ job.position }}</a>
      </div>
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
