<script setup>
defineProps({
  text: String
})
const dataTest = 'これはデータです'
</script>

<template>
  <p v-text="dataTest"></p>
</template>
