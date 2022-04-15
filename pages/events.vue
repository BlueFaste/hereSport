<template>
  <main>
    <Header></Header>
    <div>
      <Event v-for="event in events" :event="event" :key="event.id"></Event>
    </div>
  </main>
</template>

<script lang="ts">
import Vue from "vue";
import Header from "~/components/common/Header.vue";
import Event from "~/components/card/Event.vue";

export default Vue.extend({
  components: { Header, Event },
  name: "test",

  data() {
    return {
      events: [
        {
          id: 1,
          type:"Entrainement",
          date: "20220524",
          hour:"18:00",
          place: "21 rue Galieni, 49000 Angers",
        },
        {
          id: 2,
          type:"Match",
          date: "20220529",
          hour:"18:00",
          place: "21 rue Galieni, 49000 Angers",
        },
        {
          id: 3,
          type:"Entrainement",
          date: "20220603",
          hour:"18:00",
          place: "21 rue Galieni, 49000 Angers",
        },
      ],
    };
  },
});
</script>

<style></style>
