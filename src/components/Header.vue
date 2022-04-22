<template>
  <header>
    <div class="container">
      <div class="row">
        <div class="col-12 red title fw-bold d-flex align-items-center">
          <div>Boolflix <i class="fa-solid fa-star"></i></div>
        </div>

        <input
          type="text"
          placeholder="Cerca i tuoi film e serie tv"
          v-model="search"
          @keyup="$emit('ricerca', search)"
        />
      </div>
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
header {
  .title {
    height: 70px;
    background-color: black;
  }
}
.red {
  color: red;
  font-size: 1.5rem;
}
</style>
