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
  background-color: #212121;
  color: white;
  text-align: center;
  box-sizing: border-box;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
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
