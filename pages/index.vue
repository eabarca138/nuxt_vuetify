<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6" lg="3" v-for="(personaje, i) in personajes" :key="i">
        <v-card class="mx-auto" max-width="344">
          <v-img :src="personaje.image" height="200px"></v-img>

          <v-card-title>
            {{personaje.name}}
          </v-card-title>
        </v-card>

    </v-col>

  </v-row>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      personajes: []
    };
  },
  methods: {
    async getData() {
      const url = "https://rickandmortyapi.com/api/character";
      try {
        const req = await axios(url);
        this.personajes = req.data.results;
        console.log(req.data.results);
      } catch (error) {
        console.log(error);
      }
    }
  },
    created () {
      this.getData();
    },
  };
</script>
