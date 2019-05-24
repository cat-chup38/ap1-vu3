<template>
	<div id="app">
    
    <h1>Lista de Personas</h1>
    
    <ConsultarPersonas/>
    
    
	</div>
</template>

<script>
    import ConsultarPersonas from './ConsultarPersonas.vue'

    export default {
        components: {
            ConsultarPersonas
        }
    }
</script>