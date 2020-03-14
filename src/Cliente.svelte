<script>
  import Boton from "./Boton.svelte";
  
  export let cliente = {};
</script>

<style>
  .title {
    font-weight: bold;
  }
  .card {
    background-color: #6c7b95;
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
    background-color: #fdf6f6;
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
    background-color: #fdebc9;
  }

  input:required:invalid,
  input:focus:invalid {
    background-color: #c7f0db;
  }
</style>

<div class="card" on:click>
  <input bind:value={cliente.nombre} class="title" />
  <input bind:value={cliente.apellidos} class="title" />
  <input bind:value={cliente.direccion} />
  <input 
    type="number"
    min="0"
    max="999999999" 
    bind:value={cliente.telefono} />
  <slot />
</div>
