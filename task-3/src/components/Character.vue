<template>
  <div class="content__item">
    <img
      :src="
        character.image != ''
          ? character.image
          : require(`@/assets/profile.png`)
      "
      alt="Profile picture"
      class="item__picture"
    />
    <p class="item__name">{{ character.name }}</p>
    <div class="item__house">
      <div class="item__box"></div>
      <p>{{ character.house }}</p>
    </div>
    <div class="item__birthday">
      <img src="@/assets/icon-birthday-cake.svg" alt="Birthday" />
      <p>{{ character.dateOfBirth }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Character",
  props: {
    character: Object,
  },
};
</script>
