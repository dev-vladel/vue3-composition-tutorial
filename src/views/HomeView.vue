<template>
  <div class="home">
    <h1>{{ appTitle }}</h1>
    <br>

    <h4>{{ counterData.title }}:</h4>
    
    <div>
      <button @click="decreaseCounter(1)" class="btn">-1</button>
      <button @click="decreaseCounter(2)" class="btn">-2</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1, $event)" class="btn">+1</button>
      <button @click="increaseCounter(2)" class="btn">+2</button>
    </div>

    <p>This counter is {{ parity }}</p>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text">
    </div>

  </div>
</template>

<script setup>
  import { ref, reactive, computed, watch } from 'vue';

const appTitle = 'My Amazing Counter Title'

  const counterData = reactive({
    count: 0,
    title: 'My Counter'
  });

  // first one is a getter because we cannot pass nested data
  watch(() => counterData.count, (newCount, oldCount) => {
    if (newCount >= 20) {
      alert('Way to go. You made it to 20!!!')
    }
  }); 

  const parity = computed(() => {
    if (counterData.count % 2 === 0) {
      return 'even';
    }

    return 'odd';
  })

  const increaseCounter = (amount, e) => {
    console.log(e);
    counterData.count += amount;
  }

  const decreaseCounter = amount => {
    counterData.count -= amount;
  }
</script>

<style>
  .home {
    text-align: center;
    padding: 20px;
  }

  .btn, .counter {
    font-size: 40px;
    margin: 10px;
    width: 64px;  
  }

  .edit {
    margin-top: 60px;
  }
</style>