<template>
  <div id="app">
    <h1>Problema de Monty Hall</h1>
    <div class="form">
      <div class="form">
        <div v-if="!started">
          <label for="portsAmount">Quantas portas? </label>
          <input type="text" id="portsAmount" size="3" v-model.number="portsAmount" />
        </div>
        <hr>
        <div v-if="!started">
          <label for="selectedPort">Qual porta é premiada? </label>
          <input type="text" id="selectedPort" size="3" v-model.number="selectedPort" />
        </div>
        <button v-if="!started" @click="started = true">Iniciar</button>
        <button v-if="started" @click="started = false">Reiniciar</button>
      </div>
      <div class="doors" v-if="started">
        <div v-for="i in portsAmount" :key="i">
          <Door :hasGift="i === selectedPort" :number="i" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Door from "./components/Door";

export default {
  name: "App",
  components: { Door },
  data: function() {
    return {
      started: false,
      portsAmount: 3,
      selectedPort: null
    };
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}

body {
  color: #fff;
  background: linear-gradient(to right, #4568dc, #b06ab3);
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app h1 {
  border: 1px solid #0002;
  border-radius: 5px;
  background-color: #0003;
  padding: 20px;
  margin-bottom: 60px;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}
.form {
    margin-bottom: 15px;
    font-size: 1.5rem;
}

.form button {
    font-size: 0.9em;
    margin-top: 30px;
    height: 40px;;
    width: 200px;
    border-radius: 40px;
    border-color: transparent;
    color: purple;
    font-weight: bold;
    outline: none;
    box-shadow: 15px 15px 30px rgba(0, 0, 0, 0.3);
}

.form button:active {
    background-color: rgba(255, 255, 255, 0.322);
    box-shadow: inset 5px 5px 10px rgba(0, 0, 0, 0.43);
}

.form input {
    width: 120px;
    border-radius: 5px;
    font-size: 1em;
    border-color: transparent;
    background-color: rgba(255, 255, 255, 0.185)
}

.doors {
    align-self: stretch;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}
</style>