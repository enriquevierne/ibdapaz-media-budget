<script setup lang="ts">
import Budget from "./components/Budget.vue";
import FormAddItem from "./components/FormAddItem.vue";
</script>

<template>
  <div class="w-full min-h-screen p-8 from-gray-200 to-gray-400 bg-gradient-to-br">
    <span class="text-lg text-gray-900 uppercase ">Orçamentos Mídias Igreja Batista da Paz</span>
    <div class="p-12 m-auto space-y-8 max-w-screen-2xl">
      <FormAddItem />
      <Budget />
    </div>
  </div>
</template>
