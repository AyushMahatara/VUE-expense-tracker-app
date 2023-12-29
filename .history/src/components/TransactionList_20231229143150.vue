<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <li v-for="transaction in transactions" :key="transaction.id">
      {{ transaction.text }} <span>${{ transaction.amount }}</span
      ><button class="delete-btn">x</button>
    </li>
    <!-- <li class="minus">
          Cash <span>-$400</span><button class="delete-btn">x</button>
        </li> -->
  </ul>
</template>

<script>
export default {
  data() {
    return {
      transactions: [
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
      ],
    };
  },
};
</script>
