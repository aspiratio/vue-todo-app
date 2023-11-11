<script setup>
import TestComponent from '../components/TestComponent.vue'
</script>

<template>
  <div class="test">
    <TestComponent text="propsを試した" />
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .test {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
