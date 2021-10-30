<template>
  <component :class="['title', align]" :is="component">{{ text }}</component>
</template>

<script>
export default {
  name: "MyTitle",
  props: {
    text: { type: String, default: "" },
    component: { type: String, default: "h2" },
    align: {
      type: String,
      default: "left",
      validator: function(value) {
        // Значение должно соответствовать одной из этих строк
        return ["center", "left", "right"].indexOf(value) !== -1;
      }
    }
  }
};
</script>

<style scoped>
.title {
  width: 100%;
}

.center {
  text-align: center;
}

.right {
  text-align: right;
}

.left {
  text-align: left;
}
</style>
