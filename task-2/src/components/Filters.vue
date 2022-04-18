<template>
  <section class="filters grid_element">
    <input
      type="text"
      class="filters__input"
      placeholder="Wyszukaj po imieniu i nazwisku"
    />
    <select name="characters" id="character-select" class="filters__select">
      <option value="">Wszyskie postaci</option>
    </select>
    <select name="houses" id="house-select" class="filters__select">
      <option value="">Wszyskie domy</option>
    </select>
    <button class="filters__button search">
      <img src="../assets/icon-search.svg" alt="Search" />
    </button>
    <button class="filters__button clear">
      <img src="../assets/icon-clear.svg" alt="Clear" />
    </button>
  </section>
</template>