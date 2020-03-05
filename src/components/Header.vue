<template>
  <div>{{ title }}</div>
</template>
<script>
export default {
  name: "Header",
  props: {
    title: String
  }
};
</script>
<style scoped>
div {
  color: black;
  font-size: 2em;
  font-weight: bolder;
}
</style>
