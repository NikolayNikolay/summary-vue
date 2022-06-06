<template>
  <li class="list-item">
    <div>
      <p>
        <strong>{{ email }}</strong>
      </p>
      <small>{{ text }}</small>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    email: String,
    text: String,
  },
};
</script>

<style>
</style>