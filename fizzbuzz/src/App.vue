<template>
  <div id="app">
    <FizzBuzz title="FizzBuzz"
      message="※これは、Vue.jsのサンプルプロジェクトです。"/>
  </div>
</template>


<script>
import FizzBuzz from './components/FizzBuzz.vue'


export default {
  name: 'app',
  components: {
    FizzBuzz
  }
}
</script>
