<template>
  <main>
    <Header />

    <Filters />

    <Content />
  </main>
</template>

<script>
import Header from "@/components/Header.vue";
import Filters from "@/components/Filters.vue";
import Content from "@/components/Content.vue";

export default {
  name: "HomeView",
  components: {
    Header,
    Filters,
    Content,
  },
};
</script>
