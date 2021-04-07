<script>
  import Item from "./Item.svelte";

  export let grupo = "";
  export let subgrupo = "";

  let productos = [];
  let allProducts = [];
  let state = false;

  var x;

  //open json file with the name of the group
  let response;
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function () {
    if (this.readyState == 4 && this.status == 200) {
      var respuesta = JSON.parse(xhttp.responseText);
      response = respuesta;
      state = true;
      for (x in response) {
        allProducts.push(response[x]);
      }
      productos = allProducts;
    }
  };
  xhttp.open("GET", "/" + grupo.toLowerCase() + ".json", true);
  xhttp.send(response);

  //if the json file open up then the products array will be one of the cases in the switch
  $: if (state) {
    console.log("productos cargados : " + grupo + " / " + subgrupo);
    if (subgrupo) {
      if(subgrupo=='Todos'){
        productos = allProducts
      }
      else{
        productos = [];
        productos.push(response[subgrupo.toLowerCase()]);
      }
    }
  }

  //the number of columns will be determined of the size of the window.
  $: column_size = window.innerWidth > 768 ? "is-one-quarter" : "is-half";
  const mediaQueryMd = window.matchMedia("(min-width: 769px)");

  function handleResizeChange(e) {
    if (e.matches) {
      column_size = "is-one-quarter";
    } else column_size = "is-half";
  }

  mediaQueryMd.addEventListener("change", handleResizeChange);
</script>

<div class="main-products-container">
  <div class="category-container">
    <div class="columns is-multiline is-mobile">
      {#if state && productos.length > 0 && productos[0] != undefined}
        {#each productos as prods}
          {#each prods as midata}
            <div class="column {column_size}">
              <Item
                titulo={midata.titulo}
                subtitulo={midata.subtitulo}
                img={midata.img}
                precio={midata.precio}
                tipo={midata.tipo}
                tematica={midata.tematica}
                medidas={midata.medidas}
              />
            </div>
          {/each}
        {/each}
      {:else}
        <p>No hay productos.</p>
      {/if}
    </div>
  </div>
</div>

<style>
  .main-products-container {
    padding: 0;
    margin: auto;
  }
  .is-half {
    padding: 0;
  }
  .is-one-quarter {
    padding: 0;
  }
  .columns{
    margin: auto;
  }
</style>
