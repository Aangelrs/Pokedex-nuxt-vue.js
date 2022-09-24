<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="8">
      <v-card class="logo py-4 d-flex justify-center">
        <PokemonLogo />
      </v-card>
      <v-card>
        <v-card-title class="headline">
          ¡Bienvenido a la Pokedex!
        </v-card-title>
        <v-card-text>
          <p>
            Una pokedex basada en pokemon usando la PokeApi. Podra conseguir gran variedad de pokemones y tambien ver sus caracteristicas!.
          </p>
          <p>
             Vendran proximas actualizaciones para mejorar la interfaz y mas caracteristicas!  
          </p>     
          <p>
            Gracias por probar este pequeño proyecto.
          </p>
          <div class="text-xs-right">
            <em><small>&mdash; Angel Rangel</small></em>
          </div>
          <hr class="my-3" />
          <br />
          <a
            href="https://github.com/Aangelrs/Pokedex-nuxt-vue.js"
            target="_blank"
            rel="noopener noreferrer"
          >
            GitHub del proyecto.
          </a>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn color="primary" nuxt to="/pokedex"> ¡IR A LA POKEDEX! </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>
