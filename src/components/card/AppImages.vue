<template>
  <div class="avatar">
    <slot></slot>
  </div>
</template>

<script>
export default {};
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>