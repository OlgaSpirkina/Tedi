<template>
  <Navbar
    :tasks="tasks"
   />

</template>

<script>
import Navbar from './components/Navbar.vue'

export default {
  name: 'App',
  components: {
    Navbar,
  },
  data(){
    return{
      tasks: [],
    }
  },
  methods: {
    async addNavItems(){
      const res = await fetch('http://localhost:5000/navbar')
      const data = await res.json()
      return data
    },
  },
  async created(){
    this.tasks = await this.addNavItems()
  },
}
</script>

<style>
.container-horizontal{
  width: 100%;
  margin: 0;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

</style>
