<script>
export default {
  data() {
    return {
      count: 10,
      incrementAmount: 8,
      incrementTitle: 'Counter Standard',
      message: 'Hello it works!',
      message2: 'Hello it works also!',
      newCharacter: {
        name: '',
        element: []
      },
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
      characterList: [
        {
          name: 'John',
          element: ['Air', 'Earth', 'Water', 'Fire']
        },
        {
          name: 'Tommy',
          element: ['Earth']
        },
        {
          name: 'Scott',
          element: ['Fire']
        }
      ],
      favoriteList: [],
    }
  },
  computed: {
    displayTitle(){
      if (this.count > 20) {
        return 'Counter Standard - very long'
      }
      else {
        return 'Counter Standard'
      }
    },
    optimizedIncrementAmount(){
      return this.displayTitle.length * this.incrementAmount
    },

    banderStatistics(){

      const elements = ['Air', 'Earth', 'Fire', 'Water']

      const statistics = {
        Air: 0,
        Earth: 0,
        Water: 0,
        Fire: 0
      }

      this.characterList.forEach(character => {
        elements.forEach(element => {
          if (character.element.indexOf(element) > -1) {
            statistics[element] += 1
          }
        })
      })

      return statistics
    }
  },
  methods: {

    incrementCount(){
      this.count += this.optimizedIncrementAmount;
    },
    addNewCharacter(){
      this.characterList.push(this.newCharacter)
    },
    favoriteCharacter(character){
      this.favoriteList.push(character)
    },

  },


};
</script>

<template>
  <div id="app">
        <h1>Statistics</h1>
        <ul>
          <li v-for="(stat, type) in banderStatistics" :key="`bender-${stat}-${type}`">{{ type }}: {{ stat }}</li>
        </ul>
        <h1> {{ incrementTitle }} </h1>
        <p>{{ count }}</p>
        <p>{{ displayTitle }}</p>
        <p>{{ optimizedIncrementAmount }}</p>
        <button @click="incrementCount">Increment counting</button>
        <div >
          <label for="incrementAmount">Increment by: </label>
          <input type="number" v-model="incrementAmount"/>
        </div>
      
        <p>{{ films[0].title }}</p><area shape="" coords="" href="" alt="">
        <p>{{ message2 }}</p>
        <ul>
          <li v-for="(movie, index) in films" :key="`movie-${index}`">
            {{ movie.title }} {{ movie.mainActor }} 
            <p v-if="movie.earnings"> {{ movie.earnings }}</p>
            <p v-else>earnings unknown</p>
          </li>
        
        </ul>
        <hr />
        <ol>
          <li v-for="(actors, index) in films" :key="`movie-${index}`">
            <p> {{ actors.mainActor }}</p>
            <button @click="favoriteCharacter(actors.mainActor)">Favorite</button>
          </li>
        </ol>
     
      
        <br>
        <h2 v-if="favoriteList.length === 0">No favorite Character</h2>
        <h2 v-else>Favorite Characters</h2>
        <pre>
        {{ newCharacter }}
      </pre>
        <span v-for="(character, index) in characterList" :key="`comma-list-character-${index}`">
          {{ character.name }}{{ index === characterList.length - 1 ? '' : ', ' }}
        </span>
        <br>
        <label for="character-name">Name</label>
        <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter" />
     
      </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
