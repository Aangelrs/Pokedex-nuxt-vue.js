<template>
    <v-app>
        <h1>Pokedex</h1>
        <v-container>
            <v-card>
                <v-container>
                    <!--{{pokemons}}  Para mostrar todo los datos del json medainte el arreglo pokemons --> 
                    <v-row>
                        <v-col 
                        v-for="pokemon in pokemons.slice(0,150)" :key="pokemon.name"
                        cols="2"> 
                        <v-card>
                                {{ get_id(pokemon) }}
                            <v-container>
                                <v-row clas="mx-0 d-flex justify-center">
                                    <img 
                                    :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${get_id(pokemon)}.png`" 
                                    :alt="pokemon.name"
                                    width="90%" 
                                    />
                                </v-row>
                                <h2 class="text-center"> {{ pokemon.name }} </h2>
                            </v-container>
                        </v-card>

                        </v-col>
                    </v-row>
                </v-container>
            </v-card>
        </v-container>
    </v-app>
</template>

<script>
import axios from 'axios';

    export default {
        name: 'AppPokedex',
        comments:{},

        data() {
            return{
                pokemons: []
            }
        },

        mounted() {
            axios.get('https://pokeapi.co/api/v2/pokemon?limit=150').then((response) => {
                this.pokemons = response.data.results;    
            })
        },

        methods: {
            get_id(pokemon){
                return Number(pokemon.url.split("/")[6]); 
            },
        },
    };
</script>