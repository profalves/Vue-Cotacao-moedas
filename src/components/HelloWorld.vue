<template>
  <div class="hello">
    <div v-for="(item, index) in list" :key="index">
      <h2>{{item.name}}</h2>
      <h4>Compra: {{item.bid}}</h4> 
      <h4>Venda: {{item.ask}}</h4>
      <div>
        <strong>Alta:</strong> {{item.high}} | 
        <strong>Baixa:</strong> {{item.low}} | 
        <strong>Variação:</strong> {{item.varBid}} ({{item.pctChange}} %)
      </div>
      <p>{{item.create_date}}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "HelloWorld",
  data() {
    return {
      list: []
    }
  },
  methods: {
    getCotation() {
      axios.get('https://economia.awesomeapi.com.br/all')
      .then( res => {
        this.list = Object.keys(res.data).map(i => res.data[i])//.map(value => value)
      })
      .catch(e => this.list = e.response)
    }
  },
  mounted(){
    setInterval(this.getCotation(), 1000)
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
