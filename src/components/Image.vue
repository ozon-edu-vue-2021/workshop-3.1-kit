<template>
  <div :class="['image', { paranja }]">
    <img class="image-el" v-bind="$attrs" :src="src" :alt="alt" />
    <span v-if="label" :class="['label', { [labelPosition]: labelPosition }]">{{ label }}</span>
  </div>
</template>

<script>
export default {
  name: "MyImage",
  props: ["src", "alt", "paranja", "label", "labelPosition"],
  inheritAttrs: false
};
</script>

<style scoped>
.image {
  background-color: var(--grayLight);
  width: max-content;
  position: relative;
  border-radius: var(--radius);
}

.image-el {
  display: block;
}

.paranja::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: 1;
  background-color: rgba(33, 33, 33, 0.1);
}

.label {
  position: absolute;
  display: block;
  border-radius: var(--radius);
  bottom: 0;
  right: 0;
  background-color: var(--green);
  color: var(--white);
  padding: 2px 4px;
}

.label.top-left {
  top: 0;
  left: 0;
}

.label.top-right {
  top: 0;
  right: 0;
}

.label.bottom-left {
  bottom: 0;
  left: 0;
}
</style>
