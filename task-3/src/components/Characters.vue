<template>
  <section class="content">
    <div class="content__result">
      <p>Wyniki wyszukiwania ({{ this.length }})</p>
    </div>
    <div class="content__area grid_element">
      <Character
        :character="character"
        v-for="character in characters"
        :key="character.id"
      />
    </div>
  </section>
</template>

<script>
import Character from "@/components/Character.vue";

export default {
  name: "Characters",
  components: {
    Character,
  },
  props: {
    characters: Array,
    length: Number,
  },
};
</script>