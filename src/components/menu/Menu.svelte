<script>
  import Breadcrumb from "./Breadcrumb.svelte";
  import Dropdown from "./Dropdown.svelte";

  export let breadcrumb_data = [];
  export let dropdown_data = [];

  console.log(breadcrumb_data);
  console.log(dropdown_data);
</script>

<div class="menu-container">
  <Breadcrumb {breadcrumb_data} />
  <hr class="margin-none" />
  <Dropdown {dropdown_data} {breadcrumb_data} />
</div>

<style>
  .menu-container{
    padding: 0;
  }
</style>
