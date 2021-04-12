<script>
  import { onMount } from "svelte";
  import SecondaryFooter from "./SecondaryFooter.svelte";
  import TituloDiv from "./TituloDiv.svelte";
  import Masonry from "masonry-layout";

  const SPINNER_LOADING_TIME = 2500;

  let json_file = "galeria";
  let galeria = [];
  let galeriaLen;
  let state = false;
  let stateShowGallery = false;

  let modalStates = [];

  let y;

  onMount(() => {
    y = 0;
  });

  //open json file with the name of the group
  let response;
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function () {
    if (this.readyState == 4 && this.status == 200) {
      var respuesta = JSON.parse(xhttp.responseText);
      response = respuesta;
      galeria = [response.galeria];
      galeriaLen = Object.keys(galeria[0]).length;
      for (let i = 0; i < galeriaLen; i++) {
        modalStates[i] = { id: i, state: "" };
      }
      state = true;
    }
  };
  xhttp.open("GET", "/" + json_file + ".json", true);
  xhttp.send();

  $: if (state) {
    //console.log(modalStates);
    setTimeout(() => {
      stateShowGallery = true;
    }, SPINNER_LOADING_TIME);
  }

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

<svelte:window bind:scrollY={y} />

<div class="title-container">
  <TituloDiv titulo="GALERIA" />
</div>
<div class="gallery-main-container">
  <div class="gallery-back-container">
    <div class="icon" class:hide-icon={stateShowGallery}>
      <i class="fas fa-spinner" />
    </div>
  </div>
  <div class="gallery-container" class:show-container={stateShowGallery}>
    <div class="grid">
      {#if state}
        {#each galeria as arrayGal}
          {#each arrayGal as imageGallery, i}
            <div class="grid-item">
              <img
                on:load={loadMasonry}
                on:click={() => {
                  modalStates[i].state = "is-active";
                }}
                src={imageGallery.img}
                alt="imagen"
                id={i}
              />
            </div>
            <div class="modal {modalStates[i].state}">
              <div class="modal-background" />
              <div class="modal-content">
                <div class="image">
                  <img class="modal-img" src={imageGallery.img} alt="" />
                </div>
              </div>
              <button
                on:click={() => {
                  modalStates[i].state = "";
                }}
                class="modal-close is-large"
                aria-label="close"
              />
            </div>
          {/each}
        {/each}
      {/if}
    </div>

    <br />
    <br />
    <SecondaryFooter />
  </div>
</div>

<style>
  .gallery-main-container {
    position: relative;
  }
  .gallery-container {
    position: relative;
    opacity: 0;
    transition: all 0.5s;
  }
  .gallery-back-container {
    position: absolute;
    height: 100vh;
    width: 100%;
    z-index: -100;
  }
  .icon {
    position: absolute;
    top: 25%;
    left: 50%;
    font-size: 30px;
    color: #f5989d;
    animation: rotate-icon 2s linear infinite;
  }
  .hide-icon {
    display: none;
  }
  @keyframes rotate-icon {
    100% {
      transform: rotate(1turn);
    }
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
  .modal-content{
    border-radius: 8px;
    height:100%;
    width:100%;
  }
  .image {
    height: 100%;
    width: 100%;
    text-align: center;
    border-radius: 8px;
  }
  .modal-img{
    height: 100%;
    width: auto;
    object-fit: contain;
    border-radius: 8px;
  }
  @media (max-width: 768px) {
    .icon {
      font-size: 25px;
    }
  }
</style>
