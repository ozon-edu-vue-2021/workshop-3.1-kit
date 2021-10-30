<template>
  <component :is="component" :class="['container', `column-${column}`]" :style="styles">
    <slot />
  </component>
</template>

<script>
export default {
  name: "MyContainer",
  props: {
    component: { type: String, default: "div" },
    column: {
      type: [Number, String],
      default: 1
    },
    direction: {
      type: String,
      default: "row",
      validator: function(value) {
        return ["row", "column"].indexOf(value) !== -1;
      }
    },
    align: {
      type: String,
      default: "center",
      validator: function(value) {
        return ["center", "start", "end"].indexOf(value) !== -1;
      }
    },
    padding: [Number, String],
    gap: [Number, String],
    filling: String
  },
  computed: {
    styles() {
      const isRow = this.direction === "row";

      return {
        gridColumn: this.column,
        justifyContent: isRow ? this.align : undefined,
        alignItems: !isRow ? this.align : undefined,
        padding: `${this.padding}px`,
        gap: `${this.gap}px`,
        backgroundColor: this.filling
      };
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  width: 100%;
}
</style>
