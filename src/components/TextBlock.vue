<template>
  <p>
   {{ text }}
  </p>
</template>

<script>
export default {
  name: "TextBlock",
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