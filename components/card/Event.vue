<template>
  <div
    :class="`flex ${
      event.type == 'Match' ? 'bg-orange-100' : 'bg-gray-200'
    } rounded-lg h-52 items-center my-12 mx-24 relative`"
  >
    <img
      class="w-44 h-44 object-cover rounded-lg absolute -left-14"
      src="https://www.lequipe.fr/_medias/img-photo-jpg/pauline-coatanea-a-ete-tres-en-vue-face-au-montenegro-r-perrocheau-l-equipe/1500000001519040/177:144,1775:1209-828-552-75/8ce89.jpg"
    />
    <div class="pl-32 h-full flex flex-col justify-between py-5 w-full">
      <div class="flex justify-between">
      <div>
        <p>{{ event.type }}</p>
        <h2 class="text-2xl">{{ formatDate(event.date) }}</h2>
        <p class="text-xl">{{ event.hour }}</p>
        <p>{{ event.place }}</p>
      </div>
      <div class="flex px-5">
        <p v-if="event.counter" class="mx-1 px-1 h-fit bg-green-400">{{event.counter.in}}</p>
        <p v-if="event.counter" class="mx-1 px-1 h-fit bg-gray-300">{{event.counter.noResponse}}</p>
        <p v-if="event.counter" class="mx-1 px-1 h-fit bg-red-400">{{event.counter.out}}</p>
      </div>
      </div>
      <div>
        <ul class="flex justify-between w-3/5 float-right mx-8">
          <li>
            <Button
              :text="'In'"
              :background="'bg-green-400'"
              :background_hover="'bg-green-500'"
              :with="'w-20'"
              :rounded="'rounded-md'"
              @click="$emit('updateCounter',{type: 'in'})"
            ></Button>
          </li>
          <li>
            <Button
              :text="'?'"
              :background="'bg-gray-300'"
              :background_hover="'bg-gray-400'"
              :with="'w-20'"
              :rounded="'rounded-md'"
              @click="$emit('updateCounter',{type: 'noResponse'})"
            ></Button>
          </li>
          <li>
            <Button
              :text="'Out'"
              :background="'bg-red-400'"
              :background_hover="'bg-red-500'"
              :with="'w-20'"
              :rounded="'rounded-md'"
              @click="$emit('updateCounter',{type: 'out'})"
            ></Button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import m from "moment";
import Button from "../common/Button.vue";

export default Vue.extend({
  components: { Button },
  name: "EventCard",
  props: {
    event: Object,
  },

  methods: {
    formatDate: function (date: string) {
      m.locale("fr");
      return m(date).format("dddd LL");
    },
  },

});

/**
 * formatData
 * date: string
 */
</script>

<style></style>
