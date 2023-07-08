<template>
<div class="container">
    <h1>Reglas del Juego</h1>

    <div class="instrucciones">
        <h2>Al iniciar el juego aparecerá una imagen de un pokemon oculta</h2>
        <h2>Junto con 4 opciones de las cuales una  es la correcta</h2>
        <h2>Se tienen 3 intentos, si adivina en alguno de los tres intentos el puntaje sera el siguiente:</h2>
        <h2>primer intento: 5 puntos</h2>
        <h2>segundo intento: 2 puntos</h2>
        <h2>tercer intento: 1 punto</h2>
        <h3>En el caso de acertar dentro de los 3 intentos aparecerá un mensaje indicando que ha ganado el juego</h3>
        <h3>Caso contrario un mensaje indicando que fallo el juego</h3>
        <h3>Ambos mensajes iran acompañados de un botón que permititrá reiniciar el juego</h3>
    </div>
</div>
  
</template>

<script>
export default {
}
</script>

<style scoped>

.container{
    margin-top: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    color: azure;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    text-shadow:
    -1.2px -1.2px 0 #2d2af1, 
    1.2px -1.2px 0 #2d2af1, 
    -1.2px 1.2px 0 #2d2af1, 
    1.2px 1.2px 0 #2d2af1;
}

.instrucciones{
    background: rgba(42, 178, 241, 0.5);
    border: 6px double whitesmoke;
    border-radius: 12px;
    text-align: justify;
    padding: 0px 10px;
}
</style>