<template>
  <section class="filters grid_element">
    <input
      type="text"
      minlength="3"
      v-model="name"
      @change="onSearch"
      class="filters__input"
      placeholder="Wyszukaj po imieniu i nazwisku"
    />
    <select
      name="characters"
      v-model="characterType"
      @change="onSearch"
      id="character-select"
      class="filters__select"
    >
      <option value="all">Wszyskie postaci</option>
      <option value="student">Tylko uczniowie</option>
      <option value="stuff">Tylko karda nauczycielska</option>
    </select>
    <select
      name="houses"
      v-model="house"
      @change="onSearch"
      id="house-select"
      class="filters__select"
    >
      <option value="all">Wszyskie domy</option>
      <option value="Gryffindor">Gryffindor</option>
      <option value="Slytherin">Slytherin</option>
      <option value="Ravenclaw">Ravenclaw</option>
      <option value="Hufflepuff">Hufflepuff</option>
    </select>
    <button @click="onSearch" class="filters__button search">
      <img src="../assets/icon-search.svg" alt="Search" />
    </button>
    <button @click="onClear" class="filters__button clear">
      <img src="../assets/icon-clear.svg" alt="Clear" />
    </button>
  </section>
</template>

<script>
export default {
  name: "Filters",
  data() {
    return {
      name: "",
      characterType: "all",
      house: "all",
    };
  },
  methods: {
    onSearch() {
      const config = {
        name: this.name,
        characterType: this.characterType,
        house: this.house,
      };

      this.$emit("search", config);
    },
    onClear() {
      this.name = "";
      this.characterType = "all";
      this.house = "all";

      this.onSearch();
    },
  },
  mounted() {
    if (localStorage.name) this.name = localStorage.name;
    if (localStorage.characterType)
      this.characterType = localStorage.characterType;
    if (localStorage.house) this.house = localStorage.house;
  },
  watch: {
    name(newName) {
      localStorage.name = newName;
    },
    characterType(newCharacter) {
      localStorage.characterType = newCharacter;
    },
    house(newHouse) {
      localStorage.house = newHouse;
    },
  },
};
</script>