<script setup>
    import { reactive } from 'vue'
    const saarcCountries = reactive([
      { name: "Bangladesh", capital: "Dhaka" },
      { name: "Nepal", capital: "Kathmandu" },
      { name: "Bhutan", capital: "Thimphu" },
      { name: "Sri Lanka", capital: "Colombo" },
      { name: "India", capital: "New Delhi" },
      { name: "Pakistan", capital: "Islamabad" },
      { name: "Maldives", capital: "Male" }
    ])

  const capitals = ["Dhaka", "Kathmandu", "Thimphu", "Colombo", "New Delhi", "Islamabad", "Male"]

  function getScore(){
      let Score = 0;
      saarcCountries.forEach(function(country){
           if(country.answer == country.capital){
              Score++;
              console.log(Score);
           } 
      })

      return Score;
  }
</script>

<template>
     <section class="mx-auto container text-left">
      <h1 class="text-2xl mb-10">Vue Form</h1>
      <p class="mb-10">{{ saarcCountries }}</p>
      <p>Your Score: {{ getScore() }}</p>
      <div class="my-5 border border-gray-400 p-5" v-for="(countries,index) in saarcCountries" :key="index">
        <p>What is the capital of {{ countries.name }}?</p>
        <template v-for="capital in capitals">
          <input type="radio" :name="countries.name" :value="capital" v-model="countries.answer"/>
          <label class="ml-2 mr-2">{{ capital }}</label>
        </template>
      </div>
  </section>
</template>

<style scoped>

</style>
