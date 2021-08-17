<template>
  <h1>{{ title }}</h1><br>
  <input type="text" ref="name">
  <button @click="handleClick">Click Me</button>
  <br><br>
  <button @click.alt="toggleModal"  @keydown.esc="showModal = false">Show Modal ( Alt )</button>
  <button @click="toggleModalTwo">Show Modal Two</button>
  <!-- <div v-if="showModal">
    <Modal :header="header" theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign In</a>
        <a href="#">Sign Up</a>
      </template>
      <h1>Header Modal</h1>
      <p>Content Modal</p>
    </Modal>

  </div> -->
  <!-- to=".modal" bisa menggunakan id -->
  <teleport to=".modals" v-if="showModal">
    <Modal :header="header" theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign In</a>
        <a href="#">Sign Up</a>
      </template>
      <h1>Header Modal</h1>
      <p>Content Modal</p>
    </Modal>

  </teleport>

  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Header Modal Two</h1>
      <p>Content Modal Two</p>
    </Modal>

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
      showModal: false,
      showModalTwo : false
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
    },
    toggleModalTwo(){
      this.showModalTwo = !this.showModalTwo
    }
  },
  

  // components: {
  //   HelloWorld
  // }
}
</script>

<style>
#app, .modals {
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
