<template>
  <div>
    <br><br>
  
      <center>
      <div class="col-sm-3">
      <input class="form-control  me-2" type="text" placeholder="Search for a movie..." v-model="query" @keyup="getResult(query)" name="search" id="search">
      </div>
      </center>
      <br>
       <div class="row" >
 <h1 v-if="movies!=''">Search Result</h1>
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
import axios from 'axios';
export default {
    name:'Search',
    data(){
        return{
            query:'',
            movies:'',
            src:'https://image.tmdb.org/t/p/w500'

        }
    },
    methods:{
        getResult(query){
        axios.get('https://api.themoviedb.org/3/search/movie?api_key='+process.env.VUE_APP_API_KEY+'&query=' + query)
        .then(response => { 

  
              this.movies = response.data.results;
               console.log(this.results);
      
              
          })
           
        }
    }

}
</script>

<style>

</style>