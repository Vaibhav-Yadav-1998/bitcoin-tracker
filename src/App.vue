<template>
  <div id="app">
    <app-header />
    <bitcoin-card :money="rate" />
    <update-time :time="time" />
    <div id="graph">
      <price-chart :chart-data="dataCollection" :options="{responsive: true, maintainAspectRatio: false}" />
    </div>
    <div id="info">
      Bitcoin Price Changes in Last One Month
    </div>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader";
import Card from "./components/Card";
import Time from "./components/Time";
import PriceChart from "./components/PriceChart.js";
import axios from "axios";

export default {
  name: "app",
  components: {
    "app-header": AppHeader,
    "bitcoin-card": Card,
    "update-time": Time,
    PriceChart
  },
  data() {
    return {
      rate: "",
      time: "",
      dataCollection: null
    };
  },
  methods: {
    getPrice() {
      const url = "https://api.coindesk.com/v1/bpi/currentprice.json";
      axios
        .get(url)
        .then(res => {
          this.rate = res.data.bpi.USD.rate;
          this.time = res.data.time.updated;
        })
        .catch(err => {
          console.log(err);
          alert("sorry something went wrong, try again");
        });
    },

    getHistory() {
      const url = "https://api.coindesk.com/v1/bpi/historical/close.json";
      axios
        .get(url)
        .then(res => {
          console.log(res.data.bpi);
          const labels = Object.keys(res.data.bpi);
          const data = Object.values(res.data.bpi);

          console.log(labels);
          console.log(data);

          this.dataCollection = {
            labels: labels,
            datasets: [
              {
                label: "Bitcoin in USD",
                backgroundColor: "#41B883",
                data: data
              }
            ]
          };
        })
        .catch(err => {
          console.log(err);
          alert("sorry something went wrong, try again");
        });
    }
  },
  mounted() {
    this.getPrice();
    this.getHistory();
  }
};
</script>

<style>
#app {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
}

#graph {
  max-width: 900px;
  margin: 50px auto;
  text-align: center;
}

#info {
  text-align: center;
  font-weight: 600;
  margin: 20px 0;
}
</style>
