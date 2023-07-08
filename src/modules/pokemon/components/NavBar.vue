<template>
  <div>
    <router-link to="/">Bienvenida</router-link >
    <router-link  to="/juego">Juego</router-link >
    <router-link  to="/premios">Premios</router-link >
    <router-link  to="/pokemonjuego">Pokemon</router-link >
  </div>
</template>

<script>
export default {
}
</script>

<style scoped>
div {
    padding: 0 30px;
}
div a{
    position: relative;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-size: 30px;
    color: #fff;
    text-decoration: none;
    font-weight: 500;
    margin-left: 60px;
}

div a::after {
    content: '';
    position: absolute;
    left: 0;
    bottom: -6px;
    width: 100%;
    height: 3px;
    background: #fff;
    border-radius: 5px;
    transform-origin: right;
    transform: scaleX(0);
    transition: transform .5s;
}

div a:hover::after {
    transform-origin: left;
    transform: scaleX(1);
}

</style>