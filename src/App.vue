<script setup>

  import Header from './components/header.vue';
  import Balance from './components/Balance.vue';
  import IncomeExpenses from './components/IncomeExpenses.vue';
  import AddTransaction from './components/AddTransaction.vue';
  import {ref, computed} from 'vue'
  

const transactions = ref([
    {id: 1, text:'Paycheck', ammount: 700.00},
    {id: 2, text:'Water Bill', ammount: -72.83},
    {id: 3, text:'Electric Bill', ammount: -153.89},
    {id: 4, text:'Returns', ammount: 20.00},
   
  ])

  const sum = computed(()=>{
    return transactions.value.reduce((acc, x)=>{
      return acc+x.ammount
    },0)
  })

  const moneyIn = computed(()=>{
    return transactions.value
    .filter((x)=>x.ammount>0)
    .reduce((acc, x)=>{
      return acc+x.ammount
    },0)
  })

  const moneyOut = computed(()=>{
    return transactions.value
    .filter((x)=>x.ammount<0)
    .reduce((acc, x)=>{
      return acc+x.ammount
    },0)
  })


</script>


<template>
  <Header></Header>
  <div class="container">
    <Balance :total="sum"></Balance>
    <IncomeExpenses :income="moneyIn" :expense="moneyOut"></IncomeExpenses>
    <AddTransaction></AddTransaction>
  </div>

    
</template>