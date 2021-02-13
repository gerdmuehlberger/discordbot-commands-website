
<template>
  <h1>{{title}}</h1>
  <h3>bot prefix: "pahie"</h3>
  <button class="modalbutton" v-for='command in commands.commands' :key="command.name" @click="sendDataToModal(command.name, command.desc, command.args); toggleCommandModal();"> 
    {{command.name}}
  </button>

  <teleport to=".modals" v-if="showCommandModal">
    <Modal :modalheader="selectedCommand" :modaldesc="selectedCommandDescription" :modalargs="selectedCommandArgs" :darkmode="darkMode" @close="toggleCommandModal"></Modal>    
  </teleport>



</template>

<script>
import Modal from './components/Modal.vue'
import commands from './bot-commands.json';

export default {
  name: 'App',
  components: {
    Modal
  },
  
  data() {
    return {
      title: 'Pahiebot Commands:',
      commands: JSON.parse(JSON.stringify(commands)),
      selectedCommand: '',
      selectedCommandDescription:'',
      selectedCommandArgs: '',
      showCommandModal: false,
      darkMode: false
    }
  },
  methods: {
    toggleDarkMode(){
      this.darkMode = !this.darkMode
      console.log()
    },
    toggleCommandModal(){
      this.showCommandModal = !this.showCommandModal
    },
    sendDataToModal(commandname, commanddesc, commandargs) {
      this.selectedCommand = commandname;
      this.selectedCommandDescription = commanddesc;
      this.selectedCommandArgs = commandargs;
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
  color: #ffffff;
  margin-top: 60px;
}

h1{
  font-size: 5em;
  margin-bottom: 0px;
  color: #ffffff;
}
</style>