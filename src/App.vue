<template>
  <div id="app">
   <Search/>
   <UpcomingMovies/>
   <TopRatedMovies/>
  </div>
</template>

<script>

import Search from './components/Search.vue'
import TopRatedMovies from './components/TopRatedMovies.vue'
import UpcomingMovies from './components/UpcomingMovies.vue'
export default {
  name: 'App',
  components: {
   Search,
   TopRatedMovies,
   UpcomingMovies
  }
}
</script>
