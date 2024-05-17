<template>
    <div class="timer-container">
      <h1>{{ displayTime }}</h1>
      <button @click="startOrPauseTimer">{{ timerActive ? 'Pausar' : 'Iniciar' }}</button>
      <button @click="resetTimer">Resetar</button>
      <button @click="startBreak(5)">Intervalo Curto</button>
      <button @click="startBreak(15)">Intervalo Longo</button>
    </div>
</template>
  
<script>
  import { ref, computed } from 'vue';
  
  export default {
    setup() {
      const timerActive = ref(false);
      const minutes = ref(25);
      const seconds = ref(0);
      let timer = null;
  
      const displayTime = computed(() => {
        return `${minutes.value}:${seconds.value < 10 ? '0' : ''}${seconds.value}`;
      });
  
      const startOrPauseTimer = () => {
        if (timerActive.value) {
          clearInterval(timer);
        } else {
          startTimer();
        }
        timerActive.value = !timerActive.value;
      };
  
      const resetTimer = () => {
        clearInterval(timer);
        timerActive.value = false;
        minutes.value = 25; // Tempo padrão de trabalho
        seconds.value = 0;
      };
  
      const startBreak = (duration) => {
        clearInterval(timer);
        timerActive.value = false;
        minutes.value = duration;
        seconds.value = 0;
        startTimer();
      };
  
      const startTimer = () => {
        timer = setInterval(() => {
          if (seconds.value === 0) {
            if (minutes.value === 0) {
              clearInterval(timer);
              timerActive.value = false;
              // Adicione ações quando o tempo acabar
            } else {
              minutes.value--;
              seconds.value = 59;
            }
          } else {
            seconds.value--;
          }
        }, 1000);
      };
  
      return {
        displayTime,
        startOrPauseTimer,
        resetTimer,
        startBreak,
        timerActive
      };
    }
  };
</script>
  
<style scoped>
  .timer-container {
    color: white;
  }
</style>