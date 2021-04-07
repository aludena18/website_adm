<script>
  export let titulo = "TITULO AQUI";
</script>

<main>
  <div class="main-div">
    <div class="main-tittle">
      <div class="tittle">
        <h1>{titulo}</h1>
      </div>
    </div>
    <div class="main-division">
      <h2></h2>
    </div>
  </div>
</main>

<style>
  .main-div {
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0;
  }
  .main-tittle {
    position: absolute;
    padding: 0px;
    background: #fff;
  }
  .tittle {
    padding: 10px;
  }
  .tittle h1 {
    font-size: 0.75rem;
    font-weight: 700;
    color: #484848;
  }
  .main-division {
    padding: 0 10px;
    width: 100%;
  }
  .main-division h2 {
    height: 1px;
    background-color: #ccc;
  }
  @media (min-width: 769px) {
    .tittle h1 {
      font-size: 1.25rem;
    }
  }
</style>
