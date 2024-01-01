<template>
  <Header />
  <div class="container">
    <Balance :total="total" />
    <IncomeExpenses :income="+income" :expenses="+expenses" />
    <TransactionList
      :transactions="transactions"
      @transactionDeleted="handleTransactionDeleted"
    />
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
  </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpense.vue";
import AddTransaction from "./components/AddTransaction.vue";
import TransactionList from "./components/TransactionList.vue";

import { useToast } from "vue-toastification";

//reactive so ref, onmounted for local storage
import { ref, computed, onMounted } from "vue";

const toast = useToast();

const transactions = ref([
  // {
  //   id: 1,
  //   text: "Flower",
  //   amount: -20,
  // },
  // {
  //   id: 2,
  //   text: "Book",
  //   amount: 220,
  // },
]);

onMounted(() => {
  const savedTransactions = JSON.parse(localStorage.getItem("transactions"));

  if (savedTransactions) {
    transactions.value = savedTransactions;
  }
});

//get total
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});

//get income
const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});

//get Expenses
const expenses = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});

//add transaction
const handleTransactionSubmitted = (transactionData) => {
  transactions.value.push({
    id: generatedUniqueId(),
    text: transactionData.text,
    amount: transactionData.amount,
  });
  savedTransactionsToLocalStorage();
  toast.success("Transaction Added");
};

//generate id
const generatedUniqueId = () => {
  return Math.floor(Math.random() * 1000);
};

//delete transaction
const handleTransactionDeleted = (id) => {
  transactions.value = transactions.value.filter(
    (transactions) => transactions.id !== id
  );
  savedTransactionsToLocalStorage();
  toast.success("Transaction Deleted");
};

//save to local storage
const savedTransactionsToLocalStorage = () => {
  localStorage.setItem("transactions", JSON.stringify(transactions.value));
};
</script>
