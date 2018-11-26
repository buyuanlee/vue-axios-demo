<template>
  <div class="hello">
    <h3>hello，小老弟，我是axios！</h3>
    <button @click="getData">发送请求</button>
    <ul>
      <li v-for="item in items">
        {{item.title}}
      </li>
    </ul>
  </div>
</template>

<script>
  Vue.prototype.$http = axios
  import Vue from 'vue'
  import axios from 'axios'

  export default {
    name: 'HelloWorld',
    data() {
      return {
        items: []
      }
    },
    methods: {
      getData() {
        //params:指定参数。page和limit为官方的api
        this.$http.get('https://cnodejs.org/api/v1/topics', {
          params: {
            page: 1,
            limit: 10
          }
        })
          .then((res) => {
            this.items = res.data.data
            console.log(res)
          })
          .catch(function (err) {
            console.log(err)
          })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    padding: 0;
  }

  a {
    color: #42b983;
  }
</style>
