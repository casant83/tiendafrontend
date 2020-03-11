<script>
  export let producto = {};
</script>

<style>
  .title {
    font-weight: bold;
  }
  .card {
    background-color: #464159;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    border-radius: 5px;
    transition: 0.3s;
    padding: 10px;
    margin: 10px;
  }

  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.4);
  }

  input {
    background-color: #6c7b95;
    padding: 10px;
    font-size: 14px;
    color: black;
    border: 0;
    outline: none;
    margin-left: 5px;
    margin-bottom: 4px;
    max-width: 140px;
  }

  input[type="number"] {
    text-align: right;
    width: 100px;
  }
  input:focus {
    background-color: #8bbabb;
  }

  input:required:invalid,
  input:focus:invalid {
    background-color: #c7f0db;
  }
</style>

<div class="card">
  <!--bind coge el texto que introduzca el usuario en la variable artículo, declarada aquí y en el atributo nombre, igual luego con el precio-->
  <input bind:value={producto.nombre} class="title" />
  <input
    type="number"
    min="0"
    max="9999.99"
    step=".01"
    bind:value={producto.precio} />  €
  <input 
    type="number"
    min="0"
    max="9999.99"
    step=".01" 
    bind:value={producto.cantidad} />
  <input bind:value={producto.codigoProducto} />

    <!--Slot deja como un hueco en el que luego se van a poner los botones (que es un componente que puede ser distintos en cada card)-->
  <slot />
</div>
