<template>
  <div :class="['wrapper', size && `size-${size}`]">
    <p class="label">
      <label class="label-el" :for="`${type}-${id}`">{{ label }}</label>
    </p>
    <p class="input">
      <input
        class="input-el"
        v-bind="$attrs"
        :id="`${type}-${id}`"
        :type="type"
        :value="value"
        @input="inputHandler"
      />
    </p>
  </div>
</template>

<script>
const TYPES = [
  "text",
  "number",
  "email",
  "password",
  "search",
  "url",
  "tel",
  "date",
  "time",
  "range",
  "color"
];
const SIZES = ["small", "medium", "large"];
const STATES = ["valid", "invalid"];

export default {
  name: "MyInput",
  props: {
    value: { type: [String, undefined] },
    label: { type: [String, undefined] },
    type: {
      type: [String, undefined],
      validator: function(value) {
        return TYPES.indexOf(value) !== -1;
      }
    },
    id: {
      type: [String, undefined],
      required: true
    },
    size: {
      type: [String, undefined],
      validator: function(value) {
        return SIZES.indexOf(value) !== -1;
      }
    },
    state: {
      type: [String, undefined],
      validator: function(value) {
        return STATES.indexOf(value) !== -1;
      }
    }
  },
  inheritAttrs: false,
  methods: {
    inputHandler(evt) {
      this.$emit("input", evt.target.value);
    }
  }
};
</script>

<style scoped>
.wrapper {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  width: 100%;
}

.input {
  width: 100%;
  margin: 0;
}

.input-el {
  width: 100%;
  box-sizing: border-box;
  padding: 2px;
  border: 1px solid var(--gray);
  display: block;
}

.label {
  margin: 0;
}

.size-small {
  min-height: 15px;
}

.size-medium {
  min-height: 20px;
}

.size-large {
  min-height: 25px;
}
</style>
