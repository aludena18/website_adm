<script>
  import SwiperCore, {
    Navigation,
    Pagination,
    Scrollbar,
    A11y,
    Autoplay,
  } from "swiper";
  import { Swiper, SwiperSlide } from "swiper/svelte";

  SwiperCore.use([Navigation, Pagination, Scrollbar, A11y, Autoplay]);

  function slideChange(e) {
    //console.log('slide change' + e);
  }

  import { count } from "../stores/store";
  count.set("home");

  let firstBannerFile = "banner_scrap_web.png";
  let innerWidth768 = { state: false };
  let iwValue;
  let mobile = "";
  $: if (iwValue > 768 && !innerWidth768.state) {
    innerWidth768.state = true;
    //alert("ventana mayor a 768px")
    //firstBannerFile = "banner_scrap_web.png";
    mobile = "";
  } else if (iwValue < 769) {
    innerWidth768.state = false;
    //firstBannerFile = "banner_scrap_web.png";
    mobile = "is-mobile";
  }
</script>

<svelte:window bind:innerWidth={iwValue} />

  <div class="main-banner-container">
    <Swiper
      loop="true"
      spaceBetween={0}
      slidesPerView={1}
      pagination={{ clickable: true }}
      autoplay={{ delay: 500000, disableOnInteraction: true }}
      on:slideChange={slideChange}
      on:swiper={(e) => console.log(e.detail[0])}
    >
      <SwiperSlide
        ><div class="slide-img">
          <img class={mobile} src="/images/slider/banner01_2.jpg" alt="" />
          <div class="slide-titles">
            <h1 class="red-color">Cajitas Decorativas</h1>
            <h2 class="gray-color">y más en finos materiales de papelería</h2>
          </div>
          <div class="slide-extra gray-color">
            <p>#Personalizado</p>
            <p>#MiTematicaFavorita</p>
          </div>
        </div></SwiperSlide
      >
      
      >
      
    </Swiper>
  </div>

<style>
  .main-banner-container{
    width: 100%;

  }
  .red-color {
    color: #f5989d;
  }
  .gray-color {
    color: rgb(102, 102, 102);
  }
  .white-color {
    color: rgb(255, 255, 255);
  }
  .slide-img {
    position: relative;
    display: flex;
    justify-content: center;
  }
  .slide-titles {
    font-family: "Kodchasan", sans-serif;
    position: absolute;
    top: 10%;
    left: 10%;
  }
  .slide-titles h1 {
    font-weight: 700;
    font-size: 45px;
  }
  .slide-titles h2 {
    font-size: 24px;
  }
  .slide-extra {
    font-family: "Kodchasan", sans-serif;
    position: absolute;
    font-size: 20px;
    bottom: 10%;
    left: 10%;
  }
  .slide-titles2 {
    font-family: "Kodchasan", sans-serif;
    position: absolute;
    bottom: 40px;
  }

  img {
    height: 85vh;
    max-height: none;
    max-width: none;
    min-width: 100%;
    object-fit: cover;
    object-position: center;
  }
  .is-mobile {
    object-position: 75%;
  }

  @media (max-width: 1024px) {
    .slide-titles {
      top: 10%;
      left: 10%;
    }
    .slide-titles h1 {
      font-size: 40px;
    }
    .slide-titles h2 {
      font-size: 21px;
    }
    .slide-extra {
      font-size: 21px;
      bottom: 10%;
      left: 10%;
    }
  }

  @media (max-width: 769px) {
    .slide-titles {
      top:5%;     
      text-align: center;
    }
    .slide-titles h1 {
      font-size: 26px;
    }
    .slide-titles h2 {
      font-size: 16px;
    }
    .slide-extra {
      font-size: 17px;
      bottom: 5%;
      left: 5%;
    }
  }
</style>
