<template>
  <div :class="classes"></div>
</template>

<script>
export default {
  name: "Divider",
  props: {
    background: {
      type: String,
      default: "bg-black",
    },
    with: {
      type: String,
      default: "w-full",
    },
    heigth: {
      type: String,
      default: "h-0.5",
    },
    margin: {
      type: String,
      default: "mx-0 my-2",
    },
    padding: {
      type: String,
      default: "px-0 py-0",
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
      ${this.with}
      ${this.heigth}
      ${this.margin}
      ${this.padding}
      ${this.rounded ? this.rounded : ""}

      `;
    },
  },
};
</script>

<style></style>
