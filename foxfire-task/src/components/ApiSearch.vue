<template>
  <div>
    <h2>Job finder</h2>
    <input class="mb-10" v-model="search" placeholder="Search title...">
    <div v-if="info !== null" class="jobs">
      <Joboffer v-for="post in filteredList" :key="post.id" :info="post"/>
      <p v-if="filteredList.length === 0">Nothing found. :(</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Joboffer from "./Joboffer.vue";

export default {
  name: "ApiSearch",
  components: {
    Joboffer
  },
  data() {
    return {
      search: "",
      info: null
    };
  },
  mounted() {
    axios
      .get("https://api.job-dealer.de/jobs")
      .then(response => (this.info = response.data));
  },
  computed: {
    filteredList() {
      return this.info.data.filter(info => {
        return info.title.toLowerCase().includes(this.search.toLowerCase());
      });
    }
  }
};
</script>
