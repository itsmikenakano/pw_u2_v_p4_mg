<template>
  <h1 v-if="!pokemonCorrecto">Espere por favor....</h1>

  <div v-else>
    <div v-if="mostrarJuego == true">
      <h1>Juego Pokemon</h1>
      <div class="score">
        <h2>Puntaje: {{ puntaje }}</h2>
        <h2>Intentos: {{ intentos }}</h2>
      </div>
      <PokemonImg
        :pokemonId="pokemonCorrecto.id"
        :muestraPokemon="showPokemon"
      />
      <PokemonOps
        :opciones="pokemonArr"
        @seleccionado="revisarSeleccion($event)"
      />
    </div>
  </div>
  <div v-if="win == true" class="win-message">
    <h1>Felicitaciones, Ganaste!</h1>
    <h1>Tu puntuación es: {{ puntaje }}</h1>
    <PokemonImg :pokemonId="pokemonCorrecto.id" :muestraPokemon="true" />
    <button v-on:click="reiniciarJuego">Reiniciar Juego</button>
  </div>

  <div v-if="win == false && intentos == 3" class="lose-message">
    <h1>Perdiste, Has consumido todos tus intentos!</h1>
    <PokemonImg :pokemonId="pokemonCorrecto.id" :muestraPokemon="true" />
    <button v-on:click="reiniciarJuego">Reiniciar Juego</button>
  </div>
</template>

<script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps.vue";

import obtenerFachadaPokemons from "../helpers/clientePokemonAPI";

console.log();
export default {
  components: {
    PokemonImg,
    PokemonOps,
  },
  data() {
    return {
      pokemonArr: [],
      pokemonCorrecto: null,
      showPokemon: false,
      puntaje: 0,
      intentos: 0,
      win: null,
      mostrarJuego: true,
    };
  },
  methods: {
    async cargaJuegoInicial() {
      const arregloPokemons = await obtenerFachadaPokemons();
      this.pokemonArr = arregloPokemons;
      console.log(arregloPokemons);
      const indicePokemon = Math.floor(Math.random() * 4);
      this.pokemonCorrecto = this.pokemonArr[indicePokemon];
    },
    revisarSeleccion(idSeleccionado) {
      console.log("Evento del padre");
      console.log(idSeleccionado);

      if (idSeleccionado == this.pokemonCorrecto.id) {
        this.showPokemon = true;
        this.win = true;
        switch (this.intentos) {
          case 0:
            this.puntaje += 5;
            break;
          case 1:
            this.puntaje += 3;
            break;
          case 2:
            this.puntaje += 1;
            break;
        }
        this.mostrarJuego = false;
      } else {
        this.showPokemon = false;
        this.win = false;
        this.intentos++;
        if (this.intentos == 3) {
          this.mostrarJuego = false;
        }
      }
    },

    reiniciarJuego() {
      this.win = null;
      this.puntaje = 0;
      this.intentos = 0;
      this.pokemonCorrecto = null;
      this.showPokemon = false;
      this.cargaJuegoInicial();
      this.mostrarJuego = true;
    },
  },
  mounted() {
    console.log("Se monto el componente");
    this.cargaJuegoInicial();
  },
};
</script>

<style>
.score {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: row;
}

.score h2 {
  margin-left: 15px;
  margin-right: 15px;
}

.win-message button,
.lose-message button {
  border: 2px solid black;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-size: 20px;
  margin-top: 15px;
}

.win-message h1 {
  color: #44c9eb;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}

.lose-message h1 {
  color: #d51b91;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}

.win-message button:hover,
.lose-message button:hover {
  border: 2px solid rgb(255, 255, 255);
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  color: rgb(0, 0, 0);
  background: rgb(139, 252, 237);
  font-size: 20px;
  margin-top: 15px;
}
</style>