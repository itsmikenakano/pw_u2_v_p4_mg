<template>
  <div class="contenedor">
    <h1>Estos premios pueden ser tuyos</h1>
    <div class="premios">
        <div class="premio">
            <img src="../store/pikachu.jpg" alt="No se puede cargar imagen">
            <h2>Peluche Pikachu</h2>
        </div>
        <div class="premio">
            <img src="../store/charmander.jpg" alt="No se puede cargar imagen">
            <h2>Peluche Charmander</h2>
        </div>
        <div class="premio">
            <img src="../store/squirtle.jpg" alt="No se puede cargar imagen">
            <h2>Peluche Squirtle</h2>
        </div>
        <div class="premio">
            <img src="../store/bulbasaur.jpg" alt="No se puede cargar imagen">
            <h2>Peluche Bulbasaur</h2>
        </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.contenedor{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: #7ff8f0;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    text-shadow:
    -1.2px -1.2px 0 #f12a52, 
    1.2px -1.2px 0 #f12a52, 
    -1.2px 1.2px 0 #f12a52, 
    1.2px 1.2px 0 #f12a52;
}

.premios{
    display: grid;
    justify-content: center;
    align-items: center;
    padding: 0px 8px;
    grid-template-columns: repeat(2,500px);
    grid-template-rows: repeat(2,500px);
    background: rgba(250, 250, 250, 0.51);
    border: 6px double whitesmoke;
    border-radius: 12px;
    color: azure;
    text-shadow:
    -1.2px -1.2px 0 #b22af1, 
    1.2px -1.2px 0 #b22af1, 
    -1.2px 1.2px 0 #b22af1, 
    1.2px 1.2px 0 #b22af1;
}

.premio{
    border: 6px double rgb(111, 244, 180);
    border-radius: 12px;
    margin: 0px 10px;
}

.premio img{
    width: 400px;
    height: 400px;

}

.premios .premio:hover{
    background: #fba9b5;
}
</style>