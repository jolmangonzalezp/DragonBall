<template>
  <div class="logo">
    <img src="../src/assets/logo_dragonballapi.webp" alt="" />
  </div>
  <div class="content">
    <div class="cards">
      <div
        class="character"
        v-for="character in characters"
        :key="character.id"
      >
        <!-- Img Character -->
        <div class="img">
          <img :src="character.image" alt="" />
        </div>
        <div class="data">
          <!-- Name -->
          <h1>{{ character.name }}</h1>
          <!-- Type - Gender -->
          <p>{{ character.race }} - {{ character.gender }}</p>
          <!-- Ki -->
          <h3>Base Ki:</h3>
          <p>{{ character.ki }}</p>
          <h3>Total Ki:</h3>
          <p>{{ character.maxKi }}</p>
          <h3>Affiliation:</h3>
          <p>{{ character.affiliation }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      characters: [],
    };
  },
  methods: {
    async getCharacters() {
      const response = await axios.get(
        "https://dragonball-api.com/api/characters"
      );
      var data = response.data;
      this.characters = data.items;
    },
  },
  mounted() {
    this.getCharacters();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 60px;
  background: #272b33;
}

.logo {
  margin-top: 30px;
}

.content {
  width: 90%;
  margin: auto;
}

.cards {
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-wrap: wrap;
}

.character {
  width: 350px;
  height: auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-bottom: 20px;
}
.character .img {
  height: 350px;
  background: #fff;
  border-radius: 20px 20px 0 0;
  z-index: 4;
}

.character .img img {
  height: 110%;
  z-index: 10;
}

.character .img img:hover {
  height: 125%;
  z-index: 10;
}

.character .data {
  background: #000;
}

h1,
h3 {
  color: #fff;
}

p {
  color: #f9c02d;
}
</style>
