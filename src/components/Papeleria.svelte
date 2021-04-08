<script>
	import { onMount } from 'svelte';
	import Footer from './Footer.svelte';
    import Menu from "./menu/Menu.svelte";

    let breadcrumb_data = [{name:"PAPELERIA"}];
    let dropdown_data = [{name:'Letras 3D'},{name:'Toppers'},{name:'Cajitas'},{name:'Etiquetas'}];

    import { count } from '../stores/store';
	count.set("papeleria");

    let y
    onMount(()=>{
        y=0
    })
        
</script>

<svelte:window bind:scrollY={y}/>

<main>
    <Menu {breadcrumb_data} {dropdown_data}/>
    <Footer/>
</main>
