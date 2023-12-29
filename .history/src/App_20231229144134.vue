<template>
  <Header />
  <div class="container">
    <Balance />
    <IncomeExpenses />
    <TransactionList :transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpense.vue";
import AddTransaction from "./components/AddTransaction.vue";
import TransactionList from "./components/TransactionList.vue";

//reactive so ref
import { ref, computed } from "vue";
const transactions = ref([
  {
    id: 1,
    text: "Flower",
    amount: -20,
  },
  {
    id: 2,
    text: "Book",
    amount: 220,
  },
]);
</script>
