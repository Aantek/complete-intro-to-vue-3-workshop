
<template>
  <div id="app">
    <counterSection :characters="characterList"/>
    <characterList />
    <hr />
   
    <br>
    <label for="character-name">Name</label>
    <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter" />
  </div>
</template>
<script>
import counterSection from './components/counterSection.vue';
import characterList from './components/characterList.vue';

export default {
  components: {
    counterSection,
    characterList
  },
  data() {
    return {
      newCharacter: {
        name: '',
        element: []
      },
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
     
      // favoriteList: [],
    }
  },
  computed: {

    
  },
  methods: {
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
    },
    // favoriteCharacter(character) {
    //   this.favoriteList.push(character)
    // },

  },


};
</script>

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
