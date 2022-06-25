<template>
  <h1>{{ text }}</h1>
</template>

<script>
export default {
  name: "TitleBlock",
  props: {
    text: {
      type: String,
      default: false,
      required: true
    }
  }
}
</script>

<style scoped>

</style>