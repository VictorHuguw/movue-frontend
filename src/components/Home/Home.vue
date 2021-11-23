<template>
  <div class="home">
    <!-- <div class="header">
      <div class="header-text">MOVUE</div>
    </div> -->

    <div class="container-fluid">
      <div class="row justify-content-center">
        <div
          v-for="movie in movieList"
          :key="movie.id"
          class="card"
          style="width: 15rem; height: 20rem; margin-top: 5px; margin-left: 5px"
        >
          <img @click="redirectDetail(movie.id)" :src="'https://image.tmdb.org/t/p/w500/'+movie.poster_path" class="card-img-top" style="height: 318px;"/>
          <div class="card-body"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "./Home.css";

export default {
  name: "Home",
  data() {
    return {
      apiKey: "607cf92e63e2529484c42b68e8b6267c",
      movieList: [],
    };
  },
  methods: {

    redirectDetail(id){
      console.log("Click id: ",id)
    },

    getAllMovies() {
      let url =
        "https://api.themoviedb.org/3/movie/popular?api_key=607cf92e63e2529484c42b68e8b6267c&language=pt-br";

      fetch(url)
        .then((response) => {
          response.json().then((data) => {
            this.movieList = data["results"];
            console.log(this.movieList);
          });
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  mounted() {
    this.getAllMovies();
  },
};
</script>
