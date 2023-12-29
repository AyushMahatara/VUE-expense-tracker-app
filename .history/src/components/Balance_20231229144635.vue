<template>
  <h4>Your Balance</h4>
  <h1 id="balance">${{ total }}</h1>
</template>

<script setup>
import { defindProps } from "vue";

const props = defindProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
