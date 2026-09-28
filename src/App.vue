<template>
  <div class="container">
    <div class="card">
      <h1>Счётчик на Vuex</h1>
      <p class="subtitle">Пример работы со стором</p>
      
      <div class="counter-val">{{ count }}</div>

      <div class="btn-group">
        <button @click="decrement" class="btn btn-sub">-1</button>
        <button @click="reset" class="btn btn-reset">Сброс</button>
        <button @click="increment" class="btn btn-add">+1</button>
      </div>
    </div>
  </div>
</template>

<script>
import { computed } from 'vue'
import { useStore } from 'vuex'

export default {
  setup() {
    const store = useStore()

    return {
      count: computed(() => store.state.count),
      increment: () => store.commit('increment'),
      decrement: () => store.commit('decrement'),
      reset: () => store.commit('reset')
    }
  }
}
</script>

<style>
body {
  margin: 0;
  background-color: #121212;
  color: #fff;
  font-family: sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
.container {
  width: 360px;
}
.card {
  background: #1e1e2e;
  padding: 30px;
  border-radius: 16px;
  text-align: center;
  box-shadow: 0 10px 25px rgba(0,0,0,0.5);
}
h1 {
  font-size: 22px;
  margin: 0 0 5px 0;
}
.subtitle {
  color: #888;
  font-size: 14px;
  margin-bottom: 25px;
}
.counter-val {
  font-size: 56px;
  font-weight: bold;
  color: #42b883;
  margin-bottom: 25px;
}
.btn-group {
  display: flex;
  gap: 10px;
  justify-content: center;
}
.btn {
  border: none;
  padding: 10px 18px;
  border-radius: 8px;
  font-size: 15px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.2s;
}
.btn-add { background: #42b883; color: #121212; }
.btn-sub { background: #e06c75; color: #fff; }
.btn-reset { background: #3e4451; color: #fff; }
.btn:hover { opacity: 0.85; }
</style>