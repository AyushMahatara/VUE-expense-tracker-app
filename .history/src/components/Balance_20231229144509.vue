<template>
  <h4>Your Balance</h4>
  <h1 id="balance">$0.00</h1>
</template>

<script setup>
import { defindProps } from "vue";

const props = defindProps({
  total: {},
});
</script>
