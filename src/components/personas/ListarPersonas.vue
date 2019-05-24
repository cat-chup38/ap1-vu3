<template>
  <li>

    {{ persona.id }} -> {{ persona.nombre }} - {{ persona.apellido }}
    
    // Para emitir un evento que está vinculado a este elemento
    <button @click="$emit('quitarpersona', persona.id)">Eliminar</button>
  
  </li>
</template>

<script>
export default {
  // propiedades: para definir las propiedades a heredar de padre a hijo
  props: {
    persona: {
      type: Object,
      required: true
    }
  }
}
</script>