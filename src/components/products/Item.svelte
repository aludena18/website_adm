<script>
  export let titulo = "titulo";
  export let subtitulo = "subtitulo";
  export let img = "/";
  export let precio = "0";
  export let tipo = "Artículo";
  export let tematica = "Varios";
  export let medidas = "Standar";

  let isActive = "";
  let isShown = "";
  function modalActive() {
    isActive = "is-active";
    isShown = "is-shown";
  }
</script>

<div class="main-item-container">
  <div class="item-image">
    <img on:click={modalActive} alt="imagen" src={img} />
  </div>
  <div class="item-description">
    <div class="item-titulo">
      <h1>{titulo}</h1>
    </div>
    <div class="item-price">
      <p><strong>S/ {precio}</strong></p>
    </div>
  </div>
</div>

<div class="modal {isActive}">
  <div class="modal-background" />
  <div class="modal-card alg-is-large">
    <header class="modal-card-head">
      <p class="modal-card-title">{tipo.toUpperCase()}</p>
      <button
        on:click={() => {
          isActive = "";
          isShown = "";
        }}
        class="delete"
        aria-label="close"></button
      >
    </header>
    <section class="modal-card-body columns">
      <div class="column is-half-desktop is-full-mobile">
        <img src={img} alt="" />
      </div>
      <div class="column alg-modal-description">
        <h1 class="title is-3">{titulo}</h1>
        <h5 class="subtitle is-5">{medidas}</h5>
        <h3 class="subtitle is-3"><strong>S/ {precio}</strong></h3>
        <h5 class="subtitle is-5">Este artículo decorativo tipo {tipo} {tematica},
                                  esta hecho en finas cartulinas de alto gramaje y papel fotográfico
                                  brillante en capas.
        </h5>
      </div>
    </section>
  </div>
</div>

<style>
  .main-item-container {
    padding: 5px;
  }
  .item-image {
    padding: 5px;
    height: 192px;
  }
  img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
  .item-image img:hover {
    transform: scale(1.05);
    cursor: pointer;
  }
  .item-description {
    padding: 5px;
    text-align: center;
  }
  .item-titulo {
    height: 50px;
    font-size: 20px;
    line-height: 25px;
    text-align: center;
    overflow: hidden;
  }
  .item-price {
    padding: 4px 0;
    font-size: 19px;
  }
  .modal {
    z-index: 1000;
    text-align: center;
  }
  .modal .column{
    padding: 0;
  }
  .alg-modal-description{
    margin: 30px;
    text-align: left;
  }
  .alg-is-large {
    width: 80vw;
    height: 80vh;
    border-radius: 4px;
  }
  .is-shown {
    height: 80vh;
  }

  @media (max-width: 768px) {
    .item-image {
      height: 150px;
    }
    .item-titulo {
      height: auto;
      max-height: 60px;
      overflow: hidden;
      font-size: 15px;
      line-height: 20px;
    }
    .modal img{
      height: 40vh;
    }
  }
</style>
