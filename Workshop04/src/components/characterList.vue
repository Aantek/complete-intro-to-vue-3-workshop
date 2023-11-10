<template>
  <ol>
    <h2>Characters</h2>
    <li v-for="(actors, index) in films" :key="`movie-${index}`">
      <p> {{ actors.mainActor }}</p>
      <button @click="favoriteCharacter(actors.mainActor)">Favorite</button>
    </li>
  </ol>
  <h2 v-if="favoriteList.length > 0">Favorite Characters</h2>
  <h2 v-else>No favorite Character</h2>
  <li v-for="(character, index) in favoriteList" :key="`character-${index}`">
    {{ character }}
  </li>
  <ul>
  		<li v-for="(movie, index) in films" :key="`movie-${index}`">
  			{{ movie.title }} {{ movie.mainActor }} 
  			<p v-if="movie.earnings"> {{ movie.earnings }}</p>
  			<p v-else>earnings unknown</p>
  		</li>
  </ul>
 
</template>

<script>
export default {
  
  data() {
    return {
      
      favoriteList: [],
      films: [
        {
          title: "Example Movie",
          mainActor: "John Doe",
          director: "Jane Smith",
          releaseDate: "2023-10-31",
          earnings: 123
        },
        {
          title: "Example Movie2",
          mainActor: "Rober DeNiro",
          director: "Christopher Nolan",
          releaseDate: "2020-11-30",
          earnings: 110
        },
        {
          title: "Example Movie3",
          mainActor: "Luciano Africano",
          director: "Alfredo",
          releaseDate: "2022-12-02",
        }
      ],
    }
  },
  methods: {
    favoriteCharacter(character) {
      this.favoriteList.push(character)
    }

  }
}
</script>

<style>

</style>