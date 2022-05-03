<template>
  <!-- <div>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
      <h1>{{ header }}</h1> 
      <p>Welcome...</p>
      <!-- simple change div tag to teleport tag -->
      <!-- <div v-if="showModal"> -->
      <teleport to=".modals" v-if="showModal">
        <!-- using props...  :text="text"  -->
        <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal" /> -->
        <!-- fix / from />  -->
        <Modal theme="sale" @close="toggleModal" > 
          <template v-slot:links>
           <a href="#">sign up now</a>
           <a href="#">more info</a>
          </template>
          <h1>Ninja Giveaway</h1>
          <p>Grab your ninja swag for half</p>
        </Modal> 
      </teleport>
      <button @click.alt = "toggleModal">open modal (alt)</button>

      <!-- <div v-if="showModalTwo"> -->
      <!--  I test with a new teleport tag and new class 'modals2'-->
      <teleport  to=".modals2" v-if="showModalTwo">
        <!-- using props...  :text="text"  -->
        <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal" /> -->
        <!-- fix / from />  -->
        <Modal theme="" @close="toggleModalTwo" > 
          <!-- the template tag can be detele because will add default template links text -->
          <!-- <template v-slot:links> -->
           <h1>sign up to the newsletter</h1>
           <p>For update and promo codes!</p>
          <!-- </template> -->
        </Modal> 
      <!-- </div> -->
      </teleport>
      <button @click.alt = "toggleModalTwo">open modal</button>

      <!-- press ALT key and click ... -->
      <!-- <button @click.alt = "toggleModal">open modal (alt)</button> -->
      
  <!-- <input type="text" ref="name">
  <button @click="handleClick">click me</button> -->
</template>

<script>
// Challenge 
// - create an extra button to open a different modal 
// - use the same modal component but pass in a different template (slot)
// - use a different method (e.g toggleModalTwo) and data (e.g. showModalTwo)

//import HelloWorld from './components/HelloWorld.vue'
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  // components: {
  //   HelloWorld
  // }
  data() {
    return {
      title: 'My First Vue App',
      // header: 'Sign up for the Giveaway!',
      // text: 'Grab your ninja swag for half price!',
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },    
    // handleClick() {
    //   console.log(this.$refs.name);
    //   this.$refs.name.classList.add('active');
    //   this.$refs.name.focus();
    // }
  }
}
</script>

<style>
#app, #modals, #modals2 {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>