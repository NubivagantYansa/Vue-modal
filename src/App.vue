<template>
 <h1>{{ title }}</h1>
  <p>Welcome...</p>

 <div v-if="showModal">
    <Modal theme="sale" @close="toggleModal"> //@close (see child) is a 'custom event' fired from a component and listened to a parent component
      <template v-slot:links> //use template inside component to create named slots
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Ninja Givaway!</h1> // default content of modal slot
      <p>Grab your ninja swag for half price!</p>
    </Modal>
  </div>  

  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Sign up to the Newsletter</h1>
      <p>For updates and promo codes!</p>
    </Modal>
  </div>

  <button @click.alt="toggleModal">open modal (alt click)</button>
  <button @click="toggleModalTwo">open modal 2</button>
</template>


<script>
//import the modals
import Modal from './components/Modal'

export default {
  name: 'App',
  //list of components
  components: { Modal },
  //data passed in the components
  data() {
    return {
      title: 'My First Vue App!',
      showModal: false,
      showModalTwo: false,
    }
  },
  //functions used
  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
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
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
button {
  background: #bbb;
  padding: 10px;
  border: none;
  border-radius: 4px;
  margin: 10px;
  font-size: 16px;
  color: #333;
}
</style>

// challenge
//   - create an extra button to open a different modal
//   - use the same modal component but pass in a different template (slot)
//   - use a different method (e.g. toggleModalTwo) and data (e.g. showModalTwo)