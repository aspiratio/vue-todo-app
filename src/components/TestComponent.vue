<script setup>
defineProps({
  text: String
})
const dataTest = 'これはデータです'
const imageUrl = 'https://source.unsplash.com/random/200x200'
const myMethod = () => {
  alert('メソッド実行')
}
</script>

<template>
  <p>{{ dataTest }}</p>

  <p v-text="dataTest"></p>

  <img v-bind:src="imageUrl" />
  <!-- 省略した書き方 -->
  <img :src="imageUrl" />

  <button v-on:click="myMethod">メソッド実行</button>
  <!-- 省略した書き方 -->
  <button @click="myMethod">メソッド実行</button>
</template>
