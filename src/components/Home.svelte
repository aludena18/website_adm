<script>
	import Hero from './Hero.svelte';
	import Footer from './Footer.svelte';
  import { onMount } from "svelte";
  import TituloDiv from "./TituloDiv.svelte";
  import Productos from "./products/Productos.svelte";

  let y;
  onMount(() => {
    y=0;
  });
</script>

<svelte:window bind:scrollY={y} />


<div class="home-container">
  
  <Hero/>

  <div class="division-tittle">
    <TituloDiv titulo="PRODUCTOS DESTACADOS" />
  </div>
  <Productos grupo="destacados" subgrupo="" />
  <Footer/>
</div>

<style>
  .division-tittle {
    padding: 0;
  }
</style>
