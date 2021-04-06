<script>
  import Productos from "./../products/Productos.svelte";

  let subgrupo = "";
  let my_toggle = "";
  let subgrupoTitle = "Todos";
  let button = { clic: false };

  export let dropdown_data = [];
  export let breadcrumb_data = [];

  dropdown_data.splice(0,0,{name:'Todos'});

  function toggle() {
    button.clic = !button.clic;
    button.clic ? (my_toggle = "is-active") : (my_toggle = "");
  }
  function items(d) {
    let data = d;
    subgrupo = data.name;
    subgrupoTitle = data.name;
    button.clic = !button.clic;
    my_toggle = "";
    console.log(data.name);
  }
</script>

<div class="subcategory-menu">
  <div class="subcategory-menu-title">
    <p>Ver:</p>
  </div>

  <div class="dropdown {my_toggle}">
    <div class="dropdown-trigger">
      <button
        on:click={toggle}
        class="dropdown-button"
        aria-haspopup="true"
        aria-controls="dropdown-menu"
      >
        <span>{subgrupoTitle}</span>
        <span class="icon is-small">
          <i class="fas fa-angle-down" aria-hidden="true" />
        </span>
      </button>
    </div>
    <div class="dropdown-menu" id="dropdown-menu" role="menu">
      <div class="dropdown-content">
        {#if dropdown_data.length > 0}
          {#each dropdown_data as ddata, i}
            <a on:click={items(ddata)} class="dropdown-item">{ddata.name}</a>
          {/each}
        {/if}
      </div>
    </div>
  </div>
</div>

<hr class="margin-none" />

<div class="container-products">
  <Productos
    grupo={breadcrumb_data[breadcrumb_data.length - 1].name}
    {subgrupo}
  />
</div>

<style>
  .dropdown-button {
    background-color: rgb(250, 250, 250);
    width: 200px;
    height: 40px;
    padding: 0 15px;
    border-radius: 20px;
    border-color: rgb(200, 200, 200);
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .category-title {
    padding: 0px;
  }
  .subcategory-menu {
    padding: 15px 0;
    display: flex;
    align-items: center;
  }
  .subcategory-menu-title {
    padding: 0 10px;
  }
  a {
    text-decoration: none;
  }
</style>
