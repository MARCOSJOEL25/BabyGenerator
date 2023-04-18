<script setup>
import { reactive } from 'vue';

    const option = reactive({
        gender: "lgbtq+",
        popularity: "Unique",
        length: "Long"
    })
</script>


<template>
  <div class="container">
    <h1>Baby Names Generator </h1>
    <p>Choose your options and click the Find Names button below</p>
    <div class="options">
      <div class="option">
        <h2>Choose a gender</h2>
        <div class="options-buttons">
          <button :class="option.gender === 'boy' && 'active'">boy</button>
          <button :class="option.gender === 'lgbtq+' && 'active'">lgbtq+</button>
          <button :class="option.gender === 'girl' && 'active'">girl</button>
        </div>
      </div>
      <div class="option">
        <h2>Choose the name's popularity</h2>
        <div class="options-buttons">
          <button>Marcos</button>
          <button>Joel</button>
          <button>Jose</button>
        </div>
      </div>
      <div class="option">
        <h2>Choose the name's length</h2>
        <div class="options-buttons">
          <button :class="option.length === 'Short' && 'active'">Short</button>
          <button :class="option.length === 'Long' && 'active'">Long</button>
          <button :class="option.length === 'All' && 'active'">All</button>
        </div>
      </div>
    </div>
  </div>
</template>


<style>
.container {
  display: flex;
  padding: 40px;
  margin: 40px;
  border: 1px solid #000;
  flex-direction: column;
  justify-items: center;
  justify-content: center;
  text-align: center;
}

.options{
    background-color: rgb(255, 238, 236);
    padding: 1rem;
    margin: 0 auto;
    margin-top: 4rem;
    border-radius: 2rem;
    position: relative;
    width: 90%;

}

button{
    background: white;
    outline: 0.15rem solid rgb(249, 87, 89);
    border: none;
    padding: 0.75rem;
    width: 12rem;
    font-size: 1rem;
    color: rgb(27, 60, 138);
    font-weight: 200;
}

.active{
    background-color: red;
    color: white;
}
</style>
