<script setup>
import TestComponent from '../components/TestComponent.vue'

//submit
const handleMessage = (submit) => {
  console.log(submit)
}
</script>

<template>
  <div class="test">
    <TestComponent text="propsを試した" @submit="handleMessage" />
    <!-- <p>{{ receivedMessage }}</p> -->
  </div>
</template>
