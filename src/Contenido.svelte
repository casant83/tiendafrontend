<script>
  import { Route }  from "svelte-routing";
  import Inicio     from "./Inicio.svelte";
  import Productos  from "./Productos.svelte";
  import Clientes   from "./Clientes.svelte";
</script>

<style>
  main {
    padding: 20px;
    padding-top: 50px;
  }
</style>

<main id="contenido">
  <Route path="/" component={Inicio} />
  <Route path="/productos" component={Productos} />
  <Route path="/clientes" component={Clientes} />
</main>
