<template>
  <div class="card card-w70">
    <h3 v-if="summaryInfo.length === 0">
      Добавьте первый блок, чтобы увидеть результат
    </h3>
    <template v-else
      ><app-block
        v-for="item in summaryInfo"
        :key="item.id"
        :classCard="item.class"
        :textCard="item.text"
      ></app-block
    ></template>
    <button
      @click="deleteSummary"
      :disabled="summaryInfo.length === 0"
      class="btn primary"
    >
      Очистить
    </button>
  </div>
</template>

<script>
import axios from "axios";
import AppBlock from "./AppBlock.vue";

export default {
  props: {
    summaryInfo: {
      type: Array,
      required: true,
    },
  },
  emits: ["deletSummary"],
  methods: {
    async deleteSummary() {
      try {
        const data = await axios.delete(
          "https://summary-test-524f1-default-rtdb.firebaseio.com/project.json"
        );
        this.$emit("deletSummary");
      } catch (err) {
        console.log(err);
      }
    },
  },
  components: {
    AppBlock,
  },
};
</script>

<style>
</style>