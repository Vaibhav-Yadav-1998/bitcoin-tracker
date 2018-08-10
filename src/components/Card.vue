<template>
    <div class="card">
        <div class="bitcoin">
            <i class="fab fa-bitcoin"></i>
        </div>
        <div class="equal">
            <i class="fas fa-equals"></i>
        </div>
        <div class="dollar">
            <i class="fas fa-dollar-sign"></i> 
            {{money}}
        </div>
    </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    money: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.card {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  align-items: center;
  max-width: 500px;
  box-sizing: border-box;
  padding: 50px 10px;
  margin: 50px auto;
  box-shadow: 0 7px 7px rgba(0, 0, 0, 0.25), 0 3px 3px rgba(0, 0, 0, 0.22);
  border-top: 0.7px solid #eee;
}

.bitcoin {
  margin: 0 15px;
  font-size: 2.7rem;
}

.equal {
  margin: 0 15px;
  font-size: 1.5rem;
}

.dollar {
  font-size: 2rem;
  font-weight: 700;
  margin: 0 15px;
}

@media only screen and (max-width: 700px) {
  .bitcoin {
    font-size: 2rem;
  }

  .equal {
    font-size: 1rem;
  }

  .dollar {
    font-size: 1.5rem;
  }
}

@media only screen and (max-width: 334px) {
  .bitcoin {
    font-size: 1.5rem;
  }
  .equal {
    font-size: 1rem;
  }
  .dollar {
    font-size: 1rem;
    font-weight: 800;
  }
}
</style>
