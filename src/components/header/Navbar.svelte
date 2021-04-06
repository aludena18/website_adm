<script>
  import Gallery from "../Gallery.svelte";
  import About from "./../About.svelte";
  import Contact from "../Contact.svelte";
  import Header from "./Header.svelte";
  import Home from "../Home.svelte";
  import Personalizados from "./../Personalizados.svelte";
  import Papeleria from "./../Papeleria.svelte";
  import { Router, Route, Link, link } from "svelte-routing";
  import { count } from "../../stores/store";

  let navbarBorder = "border-bottom";
  let count_value;

  let navbarBurger = "";
  let navbarMenu = "";

  let button = { clic: false };

  function toggle() {
    if (window.innerWidth < 1024) {
      button.clic = !button.clic;

      button.clic
        ? ((navbarBurger = "is-active"), (navbarMenu = "is-active is-absolute"))
        : ((navbarBurger = ""), (navbarMenu = ""));
    }
  }

  let shadow = "";
  function handleScroll() {
    if (window.scrollY > 100) {
      shadow = "border-shadow";
    } else shadow = "";
  }

  count.subscribe((value) => {
    count_value = value;
    if (count_value == "home") navbarBorder = "";
    else navbarBorder = "border-bottom";
  });
</script>

<svelte:window on:scroll={handleScroll} />

<Router>
  <div class="main-container {navbarBorder} {shadow}">
    <div class="container-header-nav">
      <div class="container-header">
        <Header />
      </div>
      <div class="container-navbar ">
        <nav class="navbar is-active">
          <div class="mybrand">
            <div class="mybrand-title">
              <p>Menú</p>
            </div>
            <div class="bulmabrand">
              <div class="navbar-brand">
                <a
                  on:click={toggle}
                  role="button"
                  class="navbar-burger burger {navbarBurger}"
                  aria-label="menu"
                  aria-expanded="false"
                  data-target="navbarBasicExample"
                >
                  <span aria-hidden="true" />
                  <span aria-hidden="true" />
                  <span aria-hidden="true" />
                </a>
              </div>
            </div>
          </div>

          <div id="navbarBasicExample" class="navbar-menu {navbarMenu}">
            <div class="navbar-end">
              <a on:click={toggle} href="/" class="navbar-item" use:link>
                INICIO
              </a>
              <a
                on:click={toggle}
                href="/papeleria"
                class="navbar-item"
                use:link
              >
                PAPELERíA
              </a>
              <a on:click={toggle} href="/gallery" class="navbar-item" use:link>
                GALERÍA
              </a>

              <a on:click={toggle} href="/about" class="navbar-item" use:link>
                NOSOTROS
              </a>
              <a on:click={toggle} href="/contact" class="navbar-item" use:link>
                CONTACTO
              </a>
          
              <div class="navbar-item has-dropdown is-hoverable secondary-menu">
                <a class="navbar-link" use:link> MAS INFO </a>
                
                <div class="navbar-dropdown">
                  
                  <hr class="navbar-divider" />
                  <a class="navbar-item"> Cotizador </a>
                </div>
              </div>
            </div>
          </div>
        </nav>
      </div>
    </div>
  </div>

  <div class="container-paths">
    <Route path="/" component={Home} />
    <Route path="/papeleria" component={Papeleria} />
    <Route path="/personalizados" component={Personalizados} />
    <Route path="/gallery" component={Gallery} />
    <Route path="/about" component={About} />
    <Route path="/contact" component={Contact} />
  </div>
</Router>

<style>
  .main-container {
    background-color: #fff;
    position: fixed;
    width: 100%;
    top: 0;
    z-index: 100;
    transition: box-shadow 0.3s;
  }
  .container-header-nav {
    max-width: 1440px;
    margin: auto;
  }
  .border-bottom {
    border-bottom: 2px #f5f5f5 solid;
  }
  .border-shadow {
    box-shadow: 0px 8px 8px -5px rgba(0, 0, 0, 0.4);
  }
  .container-paths {
    padding-top: 95px;
  }
  .mybrand {
    padding: 0 15px;
    display: flex;
    align-items: center;
    justify-content: flex-end;
  }
  .mybrand-title {
    color: #484848;
    padding: 0 10px;
    font-weight: 700;
  }
  .is-absolute {
    width: 100vw;
    position: absolute;
  }
  a {
    color: #484848;
    text-decoration: none;
    font-size: 15px;
  }
  span {
    height: 2px;
  }
  p {
    margin: 0;
    padding: 0;
  }
  hr {
    padding: 0;
    margin: 0;
  }
  .container-paths {
    max-width: 1440px;
    margin: auto;
  }
  .secondary-menu{
    display: none;
  }
  @media (min-width: 1024px) {
    .mybrand-title {
      display: none;
    }
  }
  .ni:hover {
    color: hotpink;
    background-color: lightseagreen;
  }
</style>
