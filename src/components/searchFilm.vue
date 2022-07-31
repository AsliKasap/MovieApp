<template>
  <div>
    <div class="img text-center p-5">
        <i id="search-img" class="fas fa-search fa-8x"></i>
    </div>
    <div class="search-div">
      <form action="get">
        <input
          type="text"
          id="search-bar"
          class="form-control p-3"
          placeholder="Film adı girin..."
          v-model="filmName"
          @keypress.enter="searchFilm"
        />
        <button
          @click="searchFilm"
          type="button"
          class="btn btn-lg btn-block btn-outline-success form-control mt-5">
          ARAMA
        </button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filmName: "",
    };
  },
  methods: {
    searchFilm() {
      this.$emit("search-film-event", this.filmName);
      this.filmName = "";
      event.preventDefault();
    },
  },
};
</script>

<style scoped>
#search-img:hover {
  color: #bb2d3b;
}




</style>
