<template>
  <div class="avatar">
    <img :src="text">
  </div>
</template>

<script>
export default {
  name: "AvatarBlock",
  props: {
    text: {
      type: String,
      default: false,
      required: true,
    }
  }
}
</script>

<style scoped>

</style>