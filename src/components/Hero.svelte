<script>
  let iw;
  let titleSize;
</script>

<div class="hero-container">
  <div class="hero-info">
    <p class="title">Cajitas Decorativas</p>
    <p class="subtitle">Hechas en Finos Materiales</p>
  </div>
  <div class="hero-info-sub">
      <p>#Pesonalizado</p>
      <p>#MiTemáticaFavorita</p>
  </div>
</div>

<style>
  .hero-container {
    position: relative;
    height: 500px;
    overflow: hidden;
    background: url(/images/slider/banner01_2.jpg) no-repeat 75% 50%;
    background-size: cover;
  }
  .hero-info {
    margin-top: 15vh;
    margin-left: 5vw;
    text-align: left;
  }
  .title {
    color: #f5989d;
    font-size: 3.5rem;
  }
  .subtitle {
    color: #606060;
    font-size: 2.15rem;
  }
  .hero-info-sub{
      position: absolute;
      color: #606060;
      margin-left: 5vw;
      bottom: 5vh;
  }
  @media (max-width: 1024px) {
    .hero-info {
      margin-top: 15vh;
      margin-left: 5vw;
      text-align: left;
    }
    .title {
      font-size: 2.5rem;
    }
    .subtitle {
      font-size: 1.55rem;
    }
  }
  @media (max-width: 768px) {
    .hero-info {
      margin-top: 3vh;
      margin-left: 0;
      text-align: center;
    }
    .title {
      font-size: 2rem;
    }
    .subtitle {
      font-size: 1.25rem;
    }
  }
</style>
