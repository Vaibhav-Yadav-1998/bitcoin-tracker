<template>
  <div id="app">
    <app-header />   

    <div class="wrapper">
      <bitcoin-card :money="rate" />
    </div>

    <update-time :time="time" />

    <div id="refresh">
      <i role="button" title="refresh" class="fas fa-sync-alt fa-2x" @click="getPrice"></i>
    </div>

    <div class="wrapper">
      <div id="graph">
         <price-chart :chart-data="dataCollection" :options="{responsive: true, maintainAspectRatio: false}" />
      </div>
    </div>

    <div id="info">
      Bitcoin Price Changes in Last One Month
    </div>

    <footer>
      Disclaimer : This data was produced from the CoinDesk Bitcoin Price Index (USD).
      
      <div class="credit">
        This App is Made by <a href="https://github.com/vaibhav-yadav-1998" target="_blank">
            Vaibhav Yadav
        </a>
      </div>
    </footer>
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
          const labels = Object.keys(res.data.bpi);
          const data = Object.values(res.data.bpi);

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

.wrapper {
  margin: 5px 10px;
}

#refresh {
  text-align: center;
  margin: 35px;
}

#refresh i {
  cursor: pointer;
  transition: transform 0.3s;
}

#refresh i:hover {
  color: gray;
}

#refresh i:active {
  color: #41b883;
  transform: rotate(30deg);
}

#graph {
  max-width: 900px;
  margin: 50px auto;
  text-align: center;
}

#info {
  text-align: center;
  font-weight: 600;
  margin: 20px 10px;
}

footer {
  text-align: center;
  font-weight: 600;
  margin: 40px 10px;
}

.credit {
  margin: 30px 10px;
}

.credit a {
  color: #41b883;
  text-decoration: none;
}
</style>
