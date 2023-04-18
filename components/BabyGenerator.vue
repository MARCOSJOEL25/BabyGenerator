<script setup lang="ts">
import { reactive, ref } from 'vue';
import { members } from '../data'

    // const enum gender {
    //     Boy = "Boy",
    //     Girl = "Girl",
    //     lgbtqiPlus ='lgbtq+'
    // }

    // const enum popularity {
    //     Boy = "Boy",
    //     Girl = "Girl",
    //     lgbtqiPlus ='lgbtq+'
    // }

    // const enum length {
    //     SHORT = "Boy",
    //     LONG = "LONG",
    //     ALL ='ALL'
    // }

    // interface OptionState{
    //     gender: gender,
    //     popularity:popularity,
    //     length: length
    // }

    // const obj: OptionState = {
    //     gender: gender.Girl,
    //     length: length.ALL,
    //     popularity: popularity.Girl,
    // }

    const option = reactive({
        gender: "Male",
        status: "Dead",
        length: "Long"
    })

    const computedSelectChracter = () => {
        return members
            .filter( item => item.status === option.status)
            .filter( item => item.gender === option.gender)
    }

    const show = ref(false)

    const showResult = () => {
        show.value = true
    }

</script>


<template>
  <div class="container">
    <h1>Baby Names Generator </h1>
    <p>Choose your options and click the Find Names button below</p>
    <div class="options">
      <div class="option">
        <h2>Choose a gender</h2>
        <div class="options-buttons">
          <button :class="option.gender === 'Male' && 'active'" @click="option.gender = 'Male'">Male</button>
          <button :class="option.gender === 'lgbtq+' && 'active'" @click="option.gender = 'lgbtq+'">lgbtq+</button>
          <button :class="option.gender === 'Female' && 'active'" @click="option.gender = 'Female'">Female</button>
        </div>
      </div>
      <div class="option">
        <h2>Choose the name's popularity</h2>
        <div class="options-buttons">
          <button :class="option.status === 'Alive' && 'active'" @click="option.status = 'Alive'">Alive</button>
          <button :class="option.status === 'Dead' && 'active'" @click="option.status = 'Dead'">Dead</button>
        </div>
      </div>
      <div class="option">
        <h2>Choose the name's length</h2>
        <div class="options-buttons">
          <button :class="option.length === 'Short' && 'active'" @click="option.length = 'Short'">Short</button>
          <button :class="option.length === 'Long' && 'active'" @click="option.length = 'Long'">Long</button>
          <button :class="option.length === 'All' && 'active'" @click="option.length = 'All'">All</button>
        </div>
      </div>
      <button class="findButton" @click="showResult">Find button</button>
    </div>
    <div class="showNames" v-if="show">
        <div v-for="(item, index) in computedSelectChracter()" :key="index">
            <div>
                name : {{ item.name }}
            </div>
            <div>
                status : {{ item.status }}
            </div>
            <div>
                gender : {{ item.gender }}
            </div>
            <img :src="item.image" alt="">
        </div>
    </div>
  </div>
</template>


<style>

.findButton{
    background-color: rgb(249, 87, 89);
    color: white;
    border-radius: 6.2rem;
    margin-top: 40px;
    border: none;
    padding: 0.75rem 1rem;
    cursor: pointer;
    font-size: 1rem;
}
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
