<template>
  <form class="card card-w30" @submit.prevent="submitForm">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select v-model="optionsValue" id="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea v-model="areaValue" id="value" rows="3"></textarea>
    </div>

    <button :disabled="areaValue.length < 3" class="btn primary">
      Добавить
    </button>
  </form>
</template>

<script>
import axios from "axios";
export default {
  props: {
    summaryInfo: Array,
  },
  data() {
    return {
      optionsValue: "title",
      areaValue: "",
    };
  },
  methods: {
    async submitForm(value) {
      const formValue = {
        class: this.optionsValue,
        text: this.areaValue,
      };
      this.summaryInfo.push(formValue);
      try {
        const data = await axios.post(
          "https://summary-test-524f1-default-rtdb.firebaseio.com/project.json",
          formValue
        );
      } catch (error) {
        console.log(error);
      }
      this.optionsValue = "title";
      this.areaValue = "";
    },
  },
};
</script>

<style>
</style>