<script>
  import { navigate } from "svelte-routing";

  export let breadcrumb_data = [];

  function goHome() {
    navigate("/");
  }
</script>

<main>
  <nav class="breadcrumb is-small" aria-label="breadcrumbs">
    <ul>
      <li><a on:click={goHome}>INICIO</a></li>
      {#if breadcrumb_data.length > 0}
        {#each breadcrumb_data as bdata, index}
          {#if index == breadcrumb_data.length - 1}
            <li class="is-active">
              <a href="#" aria-current="page">{bdata.name}</a>
            </li>
          {:else}
            <li><a>{bdata.name}</a></li>
          {/if}
        {/each}
      {/if}
    </ul>
  </nav>

  <div class="category-title">
    <h2 class="help is-link subtitle is-5">
      {breadcrumb_data[breadcrumb_data.length - 1].name}
    </h2>
  </div>
</main>

<style>
  main {
    padding: 10px 15px;
  }
  .category-title {
    padding: 0px;
  }
  a {
    text-decoration: none;
  }
</style>
