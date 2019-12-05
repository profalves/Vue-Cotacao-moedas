<template>
  <div class="hello">
    <div class="container" v-for="(item, index) in list" :key="index">
      <div class="card">
        <h2>{{item.name}}</h2>
        <h4>Compra: {{item.bid}}</h4>
        <h4>Venda: {{item.ask}}</h4>
        <div>
          <strong>Alta:</strong>
          {{item.high}} |
          <strong>Baixa:</strong>
          {{item.low}} |
          <strong>Variação:</strong>
          {{item.varBid}} ({{item.pctChange}} %)
        </div>
        <p>{{item.create_date}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Cotacao",
  data() {
    return {
      list: []
    };
  },
  methods: {
    getCotation() {
      axios
        .get("https://economia.awesomeapi.com.br/all")
        .then(res => {
          this.list = Object.keys(res.data).map(i => res.data[i]);
        })
        .catch(e => (this.list = e.response));
    }
  },
  mounted() {
    let t = 1000;
    setInterval(() => {
      this.getCotation();
      t + 1000;
    }, t);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: inline-flex;
  justify-content: center;
}

.card {
  border-radius: 20px;
  margin: 5px;
  padding: 0 10px;
  background-color: gainsboro;
  width: 30vw;
  height: 270px;
}
@media (max-width: 700px) {
  .card {
    width: 85vw;
  }
}
</style>
