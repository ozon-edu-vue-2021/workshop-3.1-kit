<template>
  <button :class="['button', {pressed}]" :type="type" @click="startAnimating">{{ text }}</button>
</template>

<script>
export default {
  name: "MyButton",
  props: {
    /**
     * Текст кнопки
     */
    text: {
      type: String,
      default: ""
    },
    /**
     * Тип кнопки
     */
    type: {
      type: String,
      default: "button"
    }
  },
  data() {
    return {
      timer: null,
      pressed: false
    };
  },
  methods: {
    startAnimating() {
      this.$emit("click");
      this.pressed = true;

      this.timer = setTimeout(() => {
        this.stopAnimating();
      }, 800);
    },
    stopAnimating() {
      this.pressed = false;
      clearTimeout(this.timer);
    }
  }
};
</script>

<style scoped>
.button {
  background-color: var(--blue);
  color: var(--white);
  border: none;
  border-radius: var(--radius);
  padding: 8px 16px;
  padding-inline: 4px;
  cursor: pointer;
  transition: var(--transition);
  text-align: center;
  max-width: max-content;
  flex-shrink: 0;
}

.button:hover {
  background-color: var(--blueHover);
}

.button:active {
  background-color: var(--blue);
  box-shadow: 0 0 5px 0 rgba(0, 91, 255, 0.5);
}

.button:disabled {
  background-color: var(--grayDark);
}

.pressed {
  display: block;
  animation: pressed 0.4s;
}

@keyframes pressed {
  20% {
    opacity: 0.8;
  }
  80% {
    opacity: 0.5;
  }
}
</style>
