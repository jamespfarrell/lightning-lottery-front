<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Enter msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Enter from './components/Enter.vue'

export default {
  name: 'app',
  components: {
    Enter
  },
    methods: {
        getInvoice: function (event, amount) {
            axios.post(`http://localhost:8081/addinvoice`, {body: '"value" : ' + amount})
                .then(response => {
                    console.log(response.data.payment_request)
                    this.invoice = response.data.payment_request
                    this.value_invoice = amount
                })
                .catch(e => {
                    this.errors.push(e)
                })
        },
        getIfPaidSomething: function (event) {
            axios.post(`http://localhost:8081/settledinvoice`, {body: '"payment_request" : "' + this.invoice + '"'})
                .then(response => {
                    if (response.data) {
                        this.simpleNotification()
                    }
                })
                .catch(e => {
                    this.errors.push(e)
                })
        },
        simpleNotification: function (event) {
            this.$snotify.success('Payment received! Thanks!', {
                timeout: 2000,
                showProgressBar: false,
                closeOnClick: true
            })
        }
    },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
