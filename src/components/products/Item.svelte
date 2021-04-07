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

<div class="main-item-container" on:click={modalActive}>
  <div class="item-image">
    <img alt="imagen" src={img} />
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
        aria-label="close"
      />
    </header>
    <section class="modal-card-body columns modal-card-container">
      <div class="column is-half-desktop is-full-mobile">
        <img src={img} alt="" />
      </div>
      <div class="column">
        <div class="column-info">
          <h1 class="title">{titulo}</h1>
          <h5 class="subtitle is-spaced">{medidas}</h5>
          <h3 class="title is-spaced"><strong>S/ {precio}</strong></h3>
          <h5 class="subtitle">
            Este artículo decorativo tipo {tipo}
            {tematica}, esta hecho en finas cartulinas de alto gramaje y papel
            fotográfico brillante en capas.
          </h5>
        </div>
      </div>
    </section>
  </div>
</div>

<style>
  .main-item-container {
    padding: 5px;
  }
  .item-image {
    padding: 0;
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
    z-index: 100;
    text-align: center;
  }
  .modal .columns {
    margin: auto;
  }
  .modal .columns .column {
    padding: 0;
  }
  .column-info {
    text-align: left;
    padding-left: 20px;
    padding-right: 0px;
  }
  .alg-is-large {
    width: 80vw;
    height: 80vh;
    border-radius: 4px;
  }
  .is-shown {
    height: 80vh;
  }
  @media (max-width: 1024px) {
    .title {
      font-size: 1.5rem;
    }
    .subtitle {
      font-size: 1.15rem;
    }
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
    .modal img {
      height: 40vh;
    }
    .title {
      font-size: 1.25rem;
    }
    .subtitle {
      font-size: 1rem;
    }
    .modal-card-container {
      padding: 0;
    }
    .column-info {
      text-align: left;
      padding-left: 15px;
      padding-right: 15px;
    }
  }
</style>
