<template>
  <div id="app">
    <app-header />
    <bitcoin-card :money="rate" />
    <update-time :time="time" />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader";
import Card from "./components/Card";
import Time from "./components/Time";
import axios from "axios";

export default {
  name: "app",
  components: {
    "app-header": AppHeader,
    "bitcoin-card": Card,
    "update-time": Time
  },
  data() {
    return {
      rate: "",
      time: ""
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
    }
  },
  mounted() {
    this.getPrice();
  }
};
</script>

<style>
#app {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
}
</style>
