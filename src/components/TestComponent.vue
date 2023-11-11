<script setup>
import { ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated } from 'vue'
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

// ライフサイクルフック
console.log('beforeCreate フック: コンポーネントが初期化される直前')
console.log('created フック: コンポーネントが初期化された直後')
onBeforeMount(() => {
  console.log('beforeMount フック: DOMにマウントされる直前')
})
onMounted(() => {
  console.log('mounted フック: DOMにマウントされた直後')
})
onBeforeUpdate(() => {
  console.log('beforeUpdate フック: コンポーネントが再描画される直前')
})
onUpdated(() => {
  console.log('update フック: コンポーネントが再描画された直後')
})
</script>

<template>
  <p>{{ text }}</p>

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

  <button @click="$emit('submit', '子コンポーネントから送られたデータ')">Submit</button>
</template>
