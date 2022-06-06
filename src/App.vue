<template>
  <div class="container column">
    <app-form :summaryInfo="summaryInfo"></app-form>
    <app-card
      :summaryInfo="summaryInfo"
      @deletSummary="summaryInfo = []"
    ></app-card>
  </div>
  <div class="container">
    <load-comment></load-comment>
  </div>
</template>

<script>
import AppForm from "./components/AppForm.vue";
import AppCard from "./components/card/AppCard.vue";
import LoadComment from "./components/comment/LoadComment.vue";
import axios from "axios";
export default {
  data() {
    return {
      summaryInfo: [],
    };
  },
  mounted() {
    this.loadSummary();
  },
  methods: {
    async loadSummary() {
      try {
        const { data } = await axios.get(
          "https://summary-test-524f1-default-rtdb.firebaseio.com/project.json"
        );
        this.summaryInfo = Object.keys(data).map((key) => {
          return {
            id: key,
            ...data[key],
          };
        });
      } catch (err) {
        console.log(err);
      }
    },
  },
  components: { AppForm, AppCard, LoadComment },
};
</script>

<style lang="scss">
</style>
