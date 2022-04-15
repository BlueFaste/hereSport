<template>
  <button :class="classes">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
    background: {
      type: String,
      default: "bg-gray-400",
    },
    background_hover: {
      type: String,
      default: "bg-gray-500",
    },
    with: {
      type: String,
      default: "w-full",
    },
    margin: {
      type: String,
      default: "mx-2 my-1",
    },
    padding: {
      type: String,
      default: "px-3 py-1",
    },
    rounded: {
      type: String,
      default: null,
    },
  },

  computed: {
    classes() {
      return `
      ${this.background}
      hover:${this.background_hover}
      ${this.with}
      ${this.margin}
      ${this.padding}
      ${this.rounded ? this.rounded : ""}`;
    },
  },
};
</script>

<style></style>
