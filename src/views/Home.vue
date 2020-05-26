<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data(){
    return {
      info: null,
      api_response: false
    }
  },
  mounted() {
    axios
            .post('http://127.0.0.1:8000/api/login?email=test@test.ru&password=123123123')
            // .post('http://127.0.0.1:8000/api/logout')
            // .post('http://127.0.0.1:8000/api/profile')
            .then(response => {
              this.info = response;
              this.showInfo();
            })
  },
  methods: {
    showInfo() {
      console.log(document.cookie);
      console.log(this.info)
    }
  }
}
</script>
