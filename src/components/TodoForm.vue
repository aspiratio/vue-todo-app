<script setup>
import { reactive, ref } from 'vue'
import { useVuelidate } from '@vuelidate/core'
import { required } from '@vuelidate/validators'
import axios from 'axios'

const initialState = {
  task: '',
  type: null
}

const state = reactive({
  ...initialState
})

const types = ['study', 'work', 'housework', 'other']

const rules = {
  task: { required },
  type: { required }
}

const v$ = useVuelidate(rules, state)

const clear = () => {
  v$.value.$reset()

  for (const [key, value] of Object.entries(initialState)) {
    state[key] = value
  }
}

const submit = () => {
  v$.$validate
  console.log('task: ', state.task)
  console.log('type: ', state.type)

  const baseUrl =
    'https://script.google.com/macros/s/AKfycby-9U9n-Q18x3xV5bj_UQeb58bE2lEJIFx857mJSdPZzHEu544N6oe-mmvI2UktCxRQmQ/exec'

  const params = {
    task: state.task,
    type: state.type
  }

  axios
    .get(baseUrl, {
      params
    })
    .then((response) => {
      console.log('Success:', response.data)
      // 成功した場合の処理をここに追加
    })
    .catch((error) => {
      console.error('Error:', error)
      // エラーが発生した場合の処理をここに追加
    })
}
</script>

<template>
  <form>
    <v-text-field
      v-model="state.task"
      :error-messages="v$.task.$errors.map((e) => e.$message)"
      :counter="20"
      label="Task"
      required
      @input="v$.task.$touch"
      @blur="v$.task.$touch"
    ></v-text-field>

    <v-select
      v-model="state.type"
      :items="types"
      :error-messages="v$.type.$errors.map((e) => e.$message)"
      label="Type"
      required
      @change="v$.type.$touch"
      @blur="v$.type.$touch"
    ></v-select>

    <v-btn class="me-4" @click="submit"> submit </v-btn>
    <v-btn @click="clear"> clear </v-btn>
  </form>
</template>
