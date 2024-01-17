<script setup>
import {ref, nextTick, reactive, computed} from 'vue'

defineProps({
  msg: String,
  test: {
    type: String,
    default: 'test'
  }
})
const a = ref()
const count = ref(0)
const show = ref(true)
const state = reactive({
  count
})
const author = reactive({
  name: 'Mosu',
  books:[
      '123',
      '456'
  ]
})
// const publishedBooks = computed(() => author.books.length > 0 ? 'yes' : 'no')
const publishedBooks = computed(() => author.books.length > 0 ? 'yes' : 'no')
const object = {
  id: ref(1)
}
const {id} = object
const increment = async () => {
  // count.value++;
  state.count++;
  await nextTick();
  // console.log(`updated count: ${count.value}`)

}
</script>

<template>
  <h1>{{ msg }}</h1>
  <h2>{{ id }}</h2>
  <h2>{{object.id}}</h2>
  <p>{{ publishedBooks }}</p>
  <div class="card">
    <button v-bind:disabled="true" type="button" v-on:click="increment">count is {{ count }}</button>
      <p>
        Edit
        <code>components/HelloWorld.vue</code> to test HMR
      </p>
  </div>
  <p>
    Or edit a
    <code>.vue</code> file in
    <code>src/components</code>
  </p>
<!--  <img src="/Users/zouguoyang/Study/AI/stable-diffusion-webui/outputs/txt2img-images/2023-06-01/00017-1058975617.png" alt="test" />-->
  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p v-if="show" class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
  <p v-else>hidden</p>
  <button @click="count++">count is: {{ count }}</button>
  <div v-bind:id="msg">
    <p>id: {{ msg }}</p>
  </div>

  <div v-for="(book, index) in author.books" :key="book">
    <li v-if="index === 1">
      {{ book }} - {{index}}
    </li>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
