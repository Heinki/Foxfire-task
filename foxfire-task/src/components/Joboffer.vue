<template>
  <div class="job-border">
    <h3 class="text-blue mt-0 pt-10" @click="toggleMoreInformation()">{{info.title}}</h3>
    <div class="joboffer" @click="toggleMoreInformation()">
      <div class="item">
        <img :src="info.company_logo">
      </div>
      <div class="item">
        <p class="remove-margin">{{info.company_name}}</p>
        <p class="remove-margin">{{info.date.timeAgo}}</p>
        <p class="remove-margin">{{info.work_type}}</p>
        <p class="remove-margin">{{info.locations[0].city}}</p>
      </div>
    </div>
    <div class="joboffer-description">
      <div class="mr-30 ml-30" v-if="show" v-html="info.description"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Joboffer",
  props: {
    info: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      show: false
    };
  },
  methods: {
    toggleMoreInformation() {
      this.show = !this.show;
    }
  }
};
</script>
