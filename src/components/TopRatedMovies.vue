<template>
<div>

<div class="row" >
    <h1>Top Rated Movies</h1>
  <div class="col-sm-3" v-for="movie in movies" :key="movie.id">
    <div class="card">
      <div class="card-body">
           <img class="card-img-top" :src="src+movie.poster_path" alt="Card image cap" width="100" height="200">
        <h5 class="card-title">{{movie.title}}</h5>
         <div class="card-text"><b>Original Title:</b>{{movie.original_title}}</div>
         <div class="card-text"><b>Released On:</b>{{movie.release_date}}</div>
          <div class="card-text"><b>Popularity:</b>{{movie.popularity}}</div>
       
      </div>
    </div>
  </div>  
</div>

</div>

</template>

<script>
import axios from "axios";
export default {
    name:'TopRatedMovies',
    data(){
        return{
            movies:'',
            src:'https://image.tmdb.org/t/p/w500'
        }
    },
    methods:{
        getTopMovies(){
         axios.get('https://api.themoviedb.org/3/movie/top_rated?api_key='+process.env.VUE_APP_API_KEY+'&language=en-US&page=1')
         .then(response => {
             this.movies=response.data.results;
              console.log(response.data.results);
         })

         
        }
    },
    created(){
        this.getTopMovies()
    }

}
</script>

<style>

</style>