<template>
  <main>
    <Header></Header>
    <div class="m-4">
      <h1 class="text-5xl">Evénements à venir</h1>
      <div class="flex flex-col justify-center items-center">
        <div class="w-3/5">
          <ul class="flex justify-center items-center">
            <li
              class="px-3 border-2 border-transparent hover:bg-gray-100 cursor-pointer"
              v-for="equipe in equipes"
              :key="`equipe-li-${equipe.id}`"
              :id="`equipe-li-${equipe.id}`"
              @click="setToogleEquipeID(equipe.id)"
            >
              {{ equipe.name }}
            </li>
          </ul>
          <Divider></Divider>
        </div>
        <div
          class="w-3/5"
          v-for="equipe in equipes"
          :key="`equipe-${equipe.id}`"
        >
          <div
            v-show="equipe.id == toggleEquipeid"
            class="w-full flex flex-col justify-center items-center"
          >
            <Event
              v-for="event in equipe.events"
              :event="event"
              :key="event.id"
              class="w-3/5 "
              @updateCounter="updateCounter()"
            ></Event>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import Vue from "vue";
import Header from "~/components/common/Header.vue";
import Event from "~/components/card/Event.vue";
import Divider from "~/components/common/Divider.vue";

export default Vue.extend({
  components: { Header, Event, Divider },
  name: "events",

  data() {
    return {
      toggleEquipeid: 0,

      equipes: [
        {
          id: 1,
          name: "Equipe 1",
          events: [
            {
              id: 1,
              type: "Entrainement",
              date: "20220524",
              hour: "18:00",
              place: "21 rue Galieni, 49000 Angers",
              counter :{
                in : 0,
                out: 0,
                noResponse: 0,
              }
            },
            {
              id: 2,
              type: "Match",
              date: "20220529",
              hour: "18:00",
              place: "21 rue Galieni, 49000 Angers",
              counter :{
                in : 0,
                out: 0,
                noResponse: 0,
              }
            },
            {
              id: 3,
              type: "Entrainement",
              date: "20220603",
              hour: "18:00",
              place: "21 rue Galieni, 49000 Angers",
              counter :{
                in : 0,
                out: 0,
                noResponse: 0,
              }
            },
          ],
        },
        {
          id: 2,
          name: "Equipe 2",
          events: [
            {
              id: 1,
              type: "Match",
              date: "20220404",
              hour: "18:00",
              place: "21 rue Galieni, 49000 Angers",
            },
            {
              id: 2,
              type: "Match",
              date: "20220312",
              hour: "18:00",
              place: "21 rue Galieni, 49000 Angers",
            },
            {
              id: 3,
              type: "Entrainement",
              date: "20220715",
              hour: "18:00",
              place: "21 rue Galieni, 49000 Angers",
            },
          ],
        },
      ],
    };
  },

  methods: {
    setToogleEquipeID: function (id: number) {
      this.toggleEquipeid = id;
      const oldActive = document.getElementsByClassName("equipe-active");
      console.log(oldActive);

      if (oldActive.length > 0) {
        oldActive[0].classList.remove("border-b-green-500");
        oldActive[0].classList.remove("equipe-active");
      }
      const newActive = document.getElementById(`equipe-li-${id}`);
      if (newActive) {
        newActive.classList.add("border-b-green-500");
        newActive.classList.add("equipe-active");
      }
    },

    updateCounter(type: string){
      console.log(type);


    }
  },

  mounted() {
    this.setToogleEquipeID(this.equipes[0].id);
  },
});
</script>

<style></style>
