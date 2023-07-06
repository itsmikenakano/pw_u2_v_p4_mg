<template>
<div class="contenedor-opciones">



  <ul>
    <!-- <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li> -->
    <li v-for="pokemon in opciones" :key="pokemon.id"  @click="$emit('seleccionado', pokemon.id)">{{pokemon.nombre}}</li>
  </ul>

  </div>
</template>

<script>
export default {
  props:{
    opciones:{
      type:Array,
      required:true
    }
  },
  methods:{
    pruebaDeEvento(){
      console.log('prueba de evento')
    }
  } 
};
</script>

<style scoped>
ul{

  list-style: none;
}
li{

  
  border: 1px solid rgb(41, 100, 100);
  border-radius: 5px;
  background-color: white;
  margin-bottom: 10px;
  width: 200px;
  cursor: pointer;

}

li:hover{
  background-color: aqua;
}

.contenedor-opciones{
  display: flex;
  justify-content: center;
}
</style>