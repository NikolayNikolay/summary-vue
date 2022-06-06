<template>
  <p v-if="!commitFlag">
    <button @click="getLoadComment" class="btn primary">
      Загрузить комментарии
    </button>
  </p>
  <app-loader v-else-if="loaderFlag"></app-loader>
  <div v-else-if="commitFlag" class="card">
    <h2>Комментарии</h2>
    <ul class="list">
      <add-item-list
        v-for="item in commits"
        :key="item.id"
        :email="item.email"
        :text="item.body"
      ></add-item-list>
    </ul>
  </div>
</template>

<script>
import AddItemList from "./AddItemList.vue";
import AppLoader from "./AppLoader.vue";
import axios from "axios";
export default {
  data() {
    return {
      commits: [],
      commitFlag: false,
      loaderFlag: false,
    };
  },
  methods: {
    async getLoadComment() {
      try {
        this.loaderFlag = true;
        this.commitFlag = true;
        const { data } = await axios.get(
          "https://jsonplaceholder.typicode.com/comments?_limit=42"
        );
        this.commits = data;
        console.log(this.commits);
        this.loaderFlag = false;
      } catch (err) {
        console.log(err);
      }
    },
  },
  components: { AddItemList, AppLoader },
};
</script>

<style>
</style>