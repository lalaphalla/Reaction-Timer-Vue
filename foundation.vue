<template>
  <h1>{{title}}</h1>
  <input type="text" ref="name"><br/>
  <button @click="handleClick">click</button>
  <teleport to=".modals" v-if="showModal">
    <!-- <Modal :header="header" :text="text" theme="sale" showModal="showModal" @close="toggleModal"/> -->
    <Modal theme="" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Phalla Giveaway!</h1>
      <p>Grab My Price Tool for half Price</p>
    </Modal>   
  </teleport>
  <!-- Modal Two -->
  <div v-if="showModalTwo">
    
    <Modal :theme="sale" @close="toggleModalTwo">
      <template v-slot:links>
        <input type="text" placeholder="Email">
        <button>Subsribe</button>
      </template>
      
      <h1>Welcome new Customer</h1>
      <p>Today is Buy one Get one Free</p>      
    </Modal>
  </div>
    
  <button @click="toggleModal">Show Modal</button>
  <button @click="toggleModalTwo">Show Modal Two</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  data(){
    return{
      title: "Write React in Vue JS",
      header: "Sign up for the giveaway!",
      text:"Grab my price tool" ,
      showModal: false,
      showModalTwo: false,
    }
  }
  ,
  components: {
    Modal
  },
  methods: {
    handleClick(){    
      //using Ref
      console.log(this.$refs.name);
      this.$refs.name.classList.add('active')
    },
    toggleModal(){
      this.showModal = !this.showModal
    },
    toggleModalTwo(){
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
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}

</style>
