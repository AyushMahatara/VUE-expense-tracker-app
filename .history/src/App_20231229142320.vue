<template>
  <Header />
  <div class="container">
    <Balance />
    <IncomeExpenses />
    <AddTransaction />
    <TransactionList />
  </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpense.vue";
import AddTransaction from "./components/AddTransaction.vue";
import TransactionList from "./components/TransactionList.vue";
</script>
