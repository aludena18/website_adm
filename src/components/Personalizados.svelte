<script>
    import Menu from "./menu/Menu.svelte";    

    let breadcrumb_data = [{name:"PERSONALIZADOS"}];
    let dropdown_data = [{name:'Copas'},{name:'Vasos'},{name:'Tazas'},{name:'Botellas'}];

    import { count } from '../stores/store';
	count.set("personalizados");

</script>

<main>
    <Menu {breadcrumb_data} {dropdown_data}/>
</main>
