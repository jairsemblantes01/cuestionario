<template>
  <div class="question">
    <h3>{{ pregunta }}</h3>
    <div v-for="(opcion, index) in opciones" :key="index">
      <label>
        <input type="radio" :value="index" v-model="respuesta">
        {{ opcion }}
      </label>
    </div>
  </div>
</template>

<script>
export default {
  props: ['pregunta', 'opciones'],
  data() {
    return {
      respuesta: null
    }
  }
}
</script>
