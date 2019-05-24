<template>
	<div>
    <button @click.exact="obtenerPersonas">Consultar</button>
		<!--<BaseInputText v-model="newTodoText" @keydown.enter="getPersonas"/>-->
	
    <ul v-if="personas.length">
			<ListarPersonas v-for="persona in personas" :key="persona.id" :persona="persona" @quitarpersona="eliminarPersona"/>
	</ul>
    </div>
</template>

<script>
import ListarPersonas from './ListarPersonas.vue'

import axios from 'axios';


export default {
	components: {
		ListarPersonas
	},
  data () {
    return {
			newTodoText: '',
            personas: [
				    { 
              id:1,
              nombre: "ya existe 1",
              apellido: 'asdf',
				    },
				    {
              id:12,
              nombre: "ya existe 2",
              apellido: 'yiyu',
            },
            ],
            recibidos: [],
            persona: []
    }
  },
	methods: {
        obtenerPersonas() {
            const path = 'http://127.0.0.1:8000/api/v1/personas/'
            axios.get(path).then((response) => {
                    this.recibidos = response.data.results
                    
                    this.recibidos.map((persona) => {
                        this.personas.push(persona);
                    });
                })
                .catch((error) => {
                    console.log(error)
                })
        },
        eliminarPersona(id) {
			    this.personas = this.personas.filter(persona => {
				    return persona.id !== id
			    })
		    }
	}
}
</script>