<template>
  <main>
    <Header />

    <Filters v-on:search="search" />

    <Characters :characters="filteredCharacters" :length="length" />
  </main>
</template>

<script>
import Header from "@/components/Header.vue";
import Filters from "@/components/Filters.vue";
import Characters from "@/components/Characters.vue";

export default {
  name: "HomeView",
  components: {
    Header,
    Filters,
    Characters,
  },
  data() {
    return {
      characters: null,
      filteredCharacters: null,
      length: 0,
    };
  },
  methods: {
    async fetchData() {
      this.characters = null;
      const res = await fetch("http://hp-api.herokuapp.com/api/characters");
      this.characters = await res.json();
      this.length = this.characters.length;
      this.characters.sort((a, b) => (a.name > b.name ? 1 : -1));
      this.filteredCharacters = this.characters;
    },
    search(config) {
      config.house != "all"
        ? (this.filteredCharacters = this.characters.filter(
            (t) => t.house == config.house
          ))
        : (this.filteredCharacters = this.characters);

      config.characterType != "all"
        ? config.characterType == "student"
          ? (this.filteredCharacters = this.filteredCharacters.filter(
              (t) => t.hogwartsStudent == true
            ))
          : (this.filteredCharacters = this.filteredCharacters.filter(
              (t) => t.hogwartsStaff == true
            ))
        : this.filteredCharacters;

      if (config.name != "") {
        if (config.name.length < 3) {
          alert("Minimum 3 znaki");
          return;
        }
        this.filteredCharacters = this.filteredCharacters.filter((t) =>
          t.name.includes(config.name)
        );
      } else {
        this.filteredCharacters;
      }

      this.length = this.filteredCharacters.length;
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>
