<script>
  export default {
    name:'Settings',
    data() {
      return {
        workTime: 25, // Tempo padrão de trabalho
        breakTime: 5 // Tempo padrão de intervalo
      };
    }
  };
</script>

<template>
    <div>
      <label>Tempo de Trabalho (minutos):</label>
      <input type="number" v-model="workTime" min="1" />
      <label>Tempo de Intervalo (minutos):</label>
      <input type="number" v-model="breakTime" min="1" />
    </div>
</template>

<style scoped>
    .settings-container {
    background-color: #222; 
    color: white; 
    }
</style>
