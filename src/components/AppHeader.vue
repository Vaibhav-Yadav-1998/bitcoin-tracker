<template>
    <header>
        <div class="logo">
            <img src="../assets/bitcoin-logo.png" alt="">
        </div>
        <h1>
            BitCoin Tracker
        </h1>
    </header>
</template>

<script>
export default {
  name: "AppHeader"
};
</script>

<style scoped>
header {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  background-color: #42b883;
  color: white;
  text-align: center;
  padding: 1px;
  box-sizing: border-box;
  box-shadow: 3px 3px 3px silver;
}

.logo {
  padding: 0 5px;
}

.logo img {
  display: block;
  max-width: 100px;
  height: auto;
}
</style>
