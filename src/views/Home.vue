<template>
  <div>
    <div class="container" style="margin-top: 95px">
      <search-film @search-film-event="getFilmsFromApi" />
      <film-list
        :movies="movies"
        @delete-from-searchlist-event="deleteFromSearchList"
        
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import searchFilm from "../components/searchFilm.vue";
import filmList from "../components/filmList.vue";

export default {
  components: {
    searchFilm,
    filmList,
  },
  data() {
    return {
      filmName: "",
      movies: [],
      favorites: [],
    };
  },
  methods: {
    getFilmsFromApi(value) {
      if (value != "") {
        const film = value;
        axios
          .get(`https://api.themoviedb.org/3/search/movie?api_key=348088421ad3fb3a9d6e56bb6a9a8f80&query=${film}`)
          .then((get_response) => {
            this.movies = get_response.data.results.map((m) => {
              return {
                title: m.title,
                description: "popularity: " + m.popularity,
                id: m.id,
                poster:
                  m.poster_path === "N/A"
                    ? "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTJnb43MuKReMIG9fvcHJrOAupaJjzKCcEdyw&usqp=CAU"
                    : `http://image.tmdb.org/t/p/w500/${m.poster_path}`,
                isExist: false
              };
            });
          });
      }
    },
    deleteFromSearchList(movie) {
      const filmIndex = this.movies.findIndex((i) => i.id == movie.id);

      this.movies.splice(filmIndex, 1);
    },
  },
  
};
</script>


<style scoped>
#movies {
  margin-bottom: 100px;
  padding: 50px;
}
</style>
