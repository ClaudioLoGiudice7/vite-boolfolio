<script>

// IMPORT DEL COMPONENTE
import AppHeader from "./components/AppHeader.vue";

// DEFINIZIONE DEL COMPONENTE IN PAGINA
export default {
  data() {
    return {
      title: "Vue Portfolio",
    }
  },

  components: {
    AppHeader
  },
};
</script>

<template>
  <AppHeader :title="title"></AppHeader>
  <router-view></router-view>
</template>

<style lang="scss"></style>