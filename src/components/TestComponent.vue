<script setup>
defineProps({
  text: String
})
const dataTest = 'これはデータです'
const imageUrl = 'https://source.unsplash.com/random/800x800'
</script>

<template>
  <p>{{ dataTest }}</p>
  <p v-text="dataTest"></p>
  <img v-bind:src="imageUrl" />
  <!-- 省略した書き方 -->
  <img :src="imageUrl" />
</template>
