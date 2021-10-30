<template>
  <span
    class="separator"
    :style="{
      height: `${space}px`,
      backgroundColor: color
    }"
  />
</template>

<script>
export default {
  name: "MySeparator",
  props: ["space", "color"]
};
</script>

<style scoped>
.separator {
  display: block;
  width: 100%;
}
</style>
