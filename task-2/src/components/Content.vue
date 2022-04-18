<template>
  <section class="content">
    <div class="content__result">
      <p>Wyniki wyszukiwania</p>
    </div>
    <div class="content__area grid_element">
      <ContentItem />
      <ContentItem />
      <ContentItem />
      <ContentItem />
      <ContentItem />
      <ContentItem />
      <ContentItem />
      <ContentItem />
    </div>
  </section>
</template>

<script>
import ContentItem from "@/components/ContentItem.vue";

export default {
  name: "Content",
  components: {
    ContentItem,
  },
};
</script>