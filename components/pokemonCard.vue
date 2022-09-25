<template>
  <v-col cols="2">
    <v-card
      light
      color="deep-purple lighten-3"
      class="rounded-tr-xl"
      outlined
      flat
      @click="selected"
    >
      <v-toolbar dark dense flat color="grey darken-2">
        <v-toolbar-title class="caption font-weight-bold">
          {{ `${name[0].toUpperCase()}${name.slice(1)}` }}
        </v-toolbar-title>
      </v-toolbar>
      <v-card-text class="py-1 px-0">
        <v-card height="150" light rounded="0" flat class="my-0">
          <v-container fluid>
            <v-row justify="center">
              <img
                :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/home/${id}.png`"
                alt="asd"
                width="150"
              />
            </v-row>
          </v-container>
        </v-card>
      </v-card-text>
      <v-card-action>
        <v-card color="grey darken-2" flat rounded="0">
          <v-container fluid>
            <v-row justify="center">
              <v-col
                v-for="typePoke in types"
                :key="typePoke.slot"
                cols="6"
                class="px-1"
              >
                <v-btn
                  x-small
                  dark
                  block
                  :color="getColorType(typePoke.type.name)"
                >
                  {{ typePoke.type.name }}
                </v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-card>
      </v-card-action>
    </v-card>
  </v-col>
</template>
<script>
export default {
  props: {
    id: {
      type: Number,
      default: 1,
    },
    name: {
      type: String,
      default: 'nombre pokemon',
    },
  },
  data() {
    return {
      typess: [],
    }
  },
  computed: {
    types() {
      this.pokemonTypes()
      return this.typess
    },
  },
  methods: {
    pokemonTypes() {
      this.$axios
        .get('https://pokeapi.co/api/v2/pokemon/' + this.id)
        .then((response) => {
          this.typess = response.data.types
        })
    },
    selected() {
      this.$emit('show-pokemon', this.id)
    },
    getColorType(type) {
      switch (type) {
        case 'fire':
          this.backgroundPoke = 'background.png'
          return 'red'
        case 'water':
          this.backgroundPoke = 'background.png'
          return 'blue darken-1'
        case 'grass':
          this.backgroundPoke = 'background.png'
          return 'green darkeen-1'
        case 'poison':
          this.backgroundPoke = 'background.png'
          return 'deep-purple lighten-2'
        case 'flying':
          this.backgroundPoke = 'backAire.png'
          return 'blue lighten-3'
        case 'bug':
          this.backgroundPoke = 'background.png'
          return 'lime darken-1'
        case 'electric':
          this.backgroundPoke = 'background.png'
          return 'yellow darken-1'
        case 'ground':
          this.backgroundPoke = 'backTierra.png'
          return 'brown darken-2'
        case 'fairy':
          return 'pink lighten-3'
        case 'psychic':
          this.backgroundPoke = 'backpsi.png'
          return 'pink darken-1'
        case 'fighting':
          this.backgroundPoke = 'backfight.png'
          return 'orange darken-3'
        case 'dragon':
          return 'purple darken-3'
        case 'rock':
          this.backgroundPoke = 'backTierra.png'
          return 'brown lighten-3'
        case 'ice':
          this.backgroundPoke = 'backIce.png'
          return 'cyan accent-1'
        case 'dark':
          return 'grey darken-4'
        case 'steel':
          return 'grey darken-3'
        case 'ghost':
          this.backgroundPoke = 'backNight.png'
          return 'indigo darken-1'
        default:
          return 'grey lighten-1'
      }
    },
  },
}
</script>