<template>
  <div id="app">
    <PomodoroSettings />
    <Timer />
  </div>
</template>

<script>
import Timer from './components/Timer.vue';
import Settings from './components/Settings.vue';

export default {
  components: {
    Timer,
    Settings
  }
};
</script>

<style>
  #app {
    background-color: black;
    background-size: cover;
  }
</style>
