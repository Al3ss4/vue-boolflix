<template>
  <header>
    <div class="container">
      <div>Boolflix</div>

      <input
        type="text"
        placeholder="Cerca i tuoi film e serie tv"
        v-model="search"
        @keyup="$emit('ricerca', search)"
      />
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComp",
  data() {
    return {
      search: "",
    };
  },
};
</script>


<style scoped lang="scss">
</style>
