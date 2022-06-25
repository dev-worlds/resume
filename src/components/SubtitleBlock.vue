<template>
  <h2>{{ text }}</h2>
</template>

<script>
export default {
  name: "SubtitleBlock",
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