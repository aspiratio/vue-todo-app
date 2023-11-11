<script setup>
import { ref } from 'vue'
defineProps({
  text: String
})
const dataTest = 'これはデータです'
const imageUrl = 'https://source.unsplash.com/random/200x200'
const myMethod = () => {
  alert('メソッド実行')
}
const name = ref('')
const fruitsList = ['みかん', 'いちご', 'りんご']
</script>

<template>
  <p>{{ dataTest }}</p>

  <p v-text="dataTest"></p>

  <img v-bind:src="imageUrl" />
  <!-- 省略した書き方 -->
  <!-- <img :src="imageUrl" /> -->

  <button v-on:click="myMethod">メソッド実行</button>
  <!-- 省略した書き方 -->
  <!-- <button @click="myMethod">メソッド実行</button> -->

  <input type="text" id="name" v-model="name" />
  <p>入力された名前: {{ name }}</p>

  <ul>
    <li v-for="fruit in fruitsList" :key="fruit.id">{{ fruit }}</li>
  </ul>

  <!-- v-ifは非表示になる時に「削除」される。v-showは非表示になるだけなので、レンダリングしなくていい。ただしv-showにelseはない -->
  <p v-if="fruitsList[0] == 'りんご'">最初の要素はりんごです</p>
  <p v-else-if="fruitsList[1] == 'りんご'">2番目の要素はりんごです</p>
  <p v-else>3番目の要素はりんごです</p>

  <p v-show="fruitsList[0] == 'りんご'">最初の要素はりんごです</p>
</template>
