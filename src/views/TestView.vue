<script setup>
import TestComponent from '../components/TestComponent.vue'
import TestVuetify from '../components/TestVuetify.vue'

//submit
const handleMessage = (submit) => {
  console.log(submit)
}
</script>

<template>
  <div class="test">
    <TestComponent text="propsを試した" @submit="handleMessage" />
    <TestVuetify />
  </div>
</template>
