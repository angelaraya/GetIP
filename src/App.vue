<template>
  <div id='app'>
    <div class='jumbotron'>
      <h1 class='display-5'>{{headerText}}</h1>
      <p class='lead'>{{subText}}</p>
      <hr class='my-4'>
      <button v-on:click='loadIP' class='btn btn-primary'>Get your IP</button>
      <button v-on:click='sendGET' class='btn btn-warning'>Send GET</button>
      <button v-on:click='sendPOST' class='btn btn-warning'>Send POST</button>
      <button v-on:click='reset' class='btn btn-secondary'>Reset</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      headerText: 'We don\'t know your IP',
      subText: 'Click the button to get your IP'
    }
  },
  methods: {
    loadIP: function() {
      this.$http.get('http://httpbin.org/ip').then(response => {
        this.headerText = `Your IP is: ${response.data.origin}`
        this.subText = 'Congratulations'
      })
    },
    reset: function() {
      this.headerText = 'We don\'t know your IP'
      this.subText = 'Click the button to get your IP'
    },
    sendGET: function() {
      this.$http.get('http://arayaq.com:8080/?query=test').then(response => {

      })
    },
    sendPOST: function() {
      this.$http.post('http://arayaq.com:8080', {name: 'Angel'}).then(response => {

      }, response => {
        alert('Something went wrong. CORS!')
      })
    }
  }
}
</script>
