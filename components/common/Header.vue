<template>
  <header
    class="bg-gradient-to-r from-green-300 to-green-500 flex justify-between px-44 py-5 items-center"
  >
    <h1>HereSport</h1>
    <nav>
      <ul class="flex justify-between">
        <li v-for="item in nav" :key="item.name">
          <NuxtLink :to="item.link">{{ item.name }}</NuxtLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "header",

  data() {
    return {
      nav: [
        {
          name: "Element 1",
          link: "/",
        },
        {
          name: "Element 2",
          link: "/test/",
        },
      ],
    };
  },
});
</script>

<style></style>
