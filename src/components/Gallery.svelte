<script>
  import SecondaryFooter from "./SecondaryFooter.svelte";
  import TituloDiv from "./TituloDiv.svelte";
  import Masonry from "masonry-layout";

  let json_file = "galeria";
  let galeria = [];
  let state = false;
  let stateShowGallery = false;

  let isActive = "";
  let imgSrc = "";
  function modalActive(iSrc) {
    isActive = "is-active";
    imgSrc = iSrc;
  }

  //open json file with the name of the group
  let response;
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function () {
    if (this.readyState == 4 && this.status == 200) {
      var respuesta = JSON.parse(xhttp.responseText);
      response = respuesta;
      galeria = [response.galeria];
      console.log(galeria);
      state = true;
    }
  };
  xhttp.open("GET", "/" + json_file + ".json", true);
  xhttp.send();

  $:if(state)setTimeout(()=>{
    stateShowGallery = true
  },1000)

  function loadMasonry() {
    console.log("load-masony");
    var elem = document.querySelector(".grid");
    var msnry = new Masonry(elem, {
      // options
      itemSelector: ".grid-item",
      isFitWidth: true,
    });
  }
</script>

<div class="title-container">
  <TituloDiv titulo="GALERIA" />
</div>
<div class="gallery-container" class:show-container={stateShowGallery}>
  

  <div class="grid">
    {#if state}
      {#each galeria as arrayGal}
        {#each arrayGal as imageGallery, i}
          <div class="grid-item">
            <img
              on:load={loadMasonry}
              on:click={modalActive(imageGallery.img)}
              src={imageGallery.img}
              alt="imagen"
            />
          </div>
        {/each}
      {/each}
    {/if}
  </div>

  <div class="modal {isActive}">
    <div class="modal-background" />
    <div class="modal-content">
      <div class="image is-4by3">
        <img src={imgSrc} alt="" />
      </div>
    </div>
    <button
      class="modal-close is-large"
      aria-label="close"
      on:click={() => {
        isActive = "";
      }}
    />
  </div>

  <br />
  <br />
  <SecondaryFooter />
</div>

<style>
  .gallery-container {
    position: relative;
    opacity: 0;
    transition: all 3s;
  }
  .show-container {
    opacity: 1;
  }
  
  .grid {
    margin: auto;
  }
  .grid-item {
    width: 175px;
    text-align: center;
  }
  .grid-item img {
    width: 170px;
    border-radius: 20px;
  }
  .grid-item img:hover {
    cursor: pointer;
  }
  .modal {
    z-index: 1000;
  }
  .image {
    text-align: center;
  }
</style>
