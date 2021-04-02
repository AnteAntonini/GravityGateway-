<template>
  <div id="app">
    <Master></Master>
    <Slave msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Slave from './components/Slave.vue'
import Master from './components/Master.vue'

export default {
  name: 'App',
  components: {
    Slave,
    Master
  }
}
</script>
