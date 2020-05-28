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
            // .post('http://127.0.0.1:8000/api/login?email=test@test.ru&password=123123123')
            .get('http://127.0.0.1:8000/api/users?jwt=' + localStorage.getItem('jwt'))

            // .post('http://127.0.0.1:8000/api/logout')
            // .post('http://127.0.0.1:8000/api/profile')
            .then(response => {
              console.log('ads');
              this.info = response;
              this.showInfo();
            })
  },
  methods: {
    showInfo() {
      // console.log(document.cookie);

      console.log(localStorage.getItem('jwt'));

      if(this.info.data.result)
      {
          var jwt = this.info.data.params.jwt;
          localStorage.setItem('jwt', jwt);

          console.log(localStorage.getItem('jwt'));

          // jwt = this.info.data.params.jwt;
          // expireTime = this.info.data.params.expireTime;
          //
          // console.log(jwt);
          // console.log(expireTime);

          // console.log(params.jwt);
      }

    }
  }
}
</script>
