<template>
  <div class="titulo">
    <h1>Calculadora</h1>
  </div>

  <div id="myApp3" class="container">
    <div class="calculadora">
      <label id="resultado">{{ pantalla }}</label>
      <label id="resultado">{{ pantalla }}</label>
      <button
        v-for="elem in miarreglo"
        :key="elem"
        v-on:click="agregarCaracter(elem)"
      >
        {{ elem }}
      </button>
      <button class="cero" v-on:click="agregarCaracter('0')">0</button>
      <button v-on:click="calcularComputado">=</button>
      <button v-on:click="agregarCaracter('*')">*</button>
      <button id="AC" v-on:click="limpiar()">AC</button>
    </div>
  </div>
</template>

<script>
const arreglo = ["1", "2", "3", "+", "4", "5", "6", "-", "7", "8", "9", "/"];

export default {
  name: "Calculadora",
  data() {
    return {
      miarreglo: arreglo,
      pantalla: "",
    };
  },

  methods: {
    agregarCaracter(caracter) {
      this.pantalla += caracter;
    },
    limpiar() {
      this.pantalla = "";
    },
    calcular() {
      this.pantalla = eval(this.pantalla);
    },
  },

  computed: {
    calcularComputado() {
      console.log("Entro al metodo calcular computado");
      try {
        this.pantalla = eval(this.pantalla);
      } catch (error) {
        this.pantalla = "Err";
      }
    },
  },
};
</script>

<style>

.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.calculadora {
  display: grid;
  grid-template-columns: repeat(4, 75px);
  grid-template-rows: repeat(5, 45px);
  background-color: rgb(143, 223, 226);
  padding: 20px;
  border-radius: 35px;
  box-shadow: 2px 2px 15px 10px rgb(195, 190, 190);
}

.titulo {
  display: flex;
  align-items: center;
  justify-content: center;
  color: aliceblue;
}

label {
  display: flex;
  justify-content: center;
  align-items: center;
}

.cero {
  grid-column: span 2;
}

#resultado {
  border: 2px inset rgb(216, 116, 249);
  font-size: 24px;
  font-weight: bolder;
  border-radius: 20px;
  padding: 18px;
  margin-bottom: 2px;
  grid-column: span 4;
}

button {
  width: auto;
  height: 35px;
  font-size: 20px;
  margin-top: 20px;
  margin: 20px 5px 0px 5px;
  border: 2px solid #000;
  background-color: beige;
  border-radius: 15px;
}

button:hover {
  color: rgb(255, 255, 255);
  background-color: rgb(128, 0, 255);
}

#AC {
  grid-column: span 4;
}
</style>