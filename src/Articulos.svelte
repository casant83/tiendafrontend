<script>
  import { onMount, getContext } from "svelte";
  //store.js, como un almacen central de Svelte, ahí están las variables globales. 
  //El botón guarda los datos en un Json llamado jsonData (lo guarda en el onMount)=> constante porque es un array y la referencia no cambia, aunque cambie el contenido
  //al poner el $ antes del nombre de una variable es que es una variable del store.js (en memoria ram)
  import { jsonData }            from "./store.js";

  import Buscar                  from "./Buscar.svelte";
  import Articulo                from "./Articulo.svelte";
  import Boton                   from "./Boton.svelte";

  const URL = getContext("URL");

  let busqueda = "";
  let articulo = {};

  onMount(async () => {
    const response = await fetch(URL.articulos);
    const data = await response.json();
    $jsonData = data;
  });

  //REACTIVIDAD
  //$: declara una variable pero de manera que el valor de la variable se pueda cambiar en cualquier momento (reactivo)
  //"i" es ignoreCase
  $: regex = new RegExp(busqueda, "i");
  //terciario: si hay alguna letra en la búsqueda filtra
  $: datos = busqueda 
    ? $jsonData.filter(item => regex.test(item.nombre))
    : $jsonData;

</script>

<style>
  .container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: left;
    flex-wrap: wrap;
  }
</style>

<h1>ARTÍCULOS</h1>
<Buscar bind:busqueda />

<div class="container">
  <!--Aquí con el bind recojo los datos y los subo a la variable artículo-->
  <Articulo bind:articulo>
    <div style="text-align: right">
      <!--Con los valores, se pasa al fecht para subirlos a la bd-->
      <Boton documento={articulo} tipo="insertar" coleccion="articulos" />
    </div>
  </Articulo>
</div>

<div class="container">
  {#each datos as articulo}
    <Articulo {articulo}>
      <div style="text-align: right">
        <Boton documento={articulo} tipo="modificar" coleccion="articulos" />
        <Boton documento={articulo} tipo="eliminar"  coleccion="articulos" />
      </div>
    </Articulo>
  {/each}
</div>
