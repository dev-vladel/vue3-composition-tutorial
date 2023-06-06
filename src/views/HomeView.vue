<template>
  <div class="home">
    <h1>{{ appTitle }}</h1>
    <br>

    <h4>{{ counterData.title }}:</h4>
    
    <div>
      <button @click="decreaseCounter()" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter()" class="btn">+</button>
    </div>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text">
    </div>

  </div>
</template>

<script setup>
  import { ref, reactive } from 'vue';

const appTitle = 'My Amazing Counter Title'

  const counterData = reactive({
    count: 0,
    title: 'My Counter'
  });

  const increaseCounter = () => {
    counterData.count++;
  }

  const decreaseCounter = () => {
    counterData.count--;
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