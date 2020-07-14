<template>
  <div id="app">
    <h1>Monty Hall Problem</h1>
    <div class="form">
      <div v-if="!started">
        <label for="doorsAmount">How many doors</label>
        <input type="number" id="doorsAmount" size="3" v-model.number="doorsAmount" />
      </div>
      <div v-if="!started">
        <label for="selectedDoor">Which is the winning door?</label>
        <input type="number" id="selectedDoor" size="3" v-model.number="selectedDoor" />
      </div>
      <button v-if="!started" @click="started = true">Start</button>
      <button v-else @click="started = false">Restart</button>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in doorsAmount" :key="i">
        <Door :hasGift="i === selectedPort" :number="i" />
      </div>
    </div>
  </div>
</template>

<script>
import Door from './components/Door'

export default {
  name: 'App',
  components: {
    Door
  },
  data() {
    return {
      started: false,
      doorsAmount: 3,
      selectedDoor: null
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}

body {
  background: linear-gradient(to right, rgb(21, 153, 87), rgb(21, 87, 153));
  color: #fff;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  background-color: #0004;
  border: 1px solid #000;
  margin-bottom: 40px;
  padding: 10px 15px;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}

.form, .form input, .form button {
  font-size: 1.5rem;
  margin-bottom: 10px;
}

.form input {
  margin-left: 10px;
}

.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
