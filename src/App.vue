<template>
  <h1>{{ title }}</h1><br>
  <input type="text" ref="name">
  <button @click="handleClick">Click Me</button>
  <br><br>
  <button @click="toggleModal"  @keydown.esc="showModal = false">Show Modal</button>
  <div v-if="showModal">
    <Modal :header="header" content="Modal Content" theme="sale" @close="toggleModal"/>

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Modal from './components/Modal.vue'
// global css dapat di import dalam component yang akan menggunakannya atau di main.js
// import './assets/css/global.css'
export default {
  name: 'App',
  components: {
    Modal
  },
  data(){
    return {
      title: 'My First Vue App',
      header: ['Header Modal', 1],
      showModal: false
    }
  },
  methods: {
    handleClick(){
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
      this.$refs.name.value = 'oke'
    },
    toggleModal(){
      this.showModal = !this.showModal
    }
  },
  

  // components: {
  //   HelloWorld
  // }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
