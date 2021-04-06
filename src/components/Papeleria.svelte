<script>
	import Footer from './Footer.svelte';
    import Menu from "./menu/Menu.svelte";

    let breadcrumb_data = [{name:"PAPELERIA"}];
    let dropdown_data = [{name:'Letras 3D'},{name:'Toppers'},{name:'Cajitas'},{name:'Etiquetas'}];

    import { count } from '../stores/store';
	count.set("papeleria");
        
</script>

<main>
    <Menu {breadcrumb_data} {dropdown_data}/>
    <Footer/>
</main>
