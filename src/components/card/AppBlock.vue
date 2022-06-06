<template>
  <app-title v-if="classCard === 'title'">{{ textCard }}</app-title>
  <app-images v-else-if="classCard === 'avatar'"
    ><img :src="textCard" alt="#"
  /></app-images>
  <app-subtitle v-else-if="classCard === 'subtitle'">{{
    textCard
  }}</app-subtitle>
  <app-text v-else-if="classCard === 'text'">{{ textCard }}</app-text>
</template>

<script>
import AppTitle from "./AppTitle.vue";
import AppSubtitle from "./AppSubtitle.vue";
import AppImages from "./AppImages.vue";
import AppText from "./AppText.vue";
export default {
  props: ["classCard", "textCard"],
  components: {
    AppTitle,
    AppText,
    AppSubtitle,
    AppImages,
  },
};
</script>

<style>
</style>