<script setup>
import { ref, onMounted } from "vue";
import { supabase } from "../lib/supabaseClient";
import { PencilSquareIcon, TrashIcon } from "@heroicons/vue/24/outline";

const formatter = new Intl.NumberFormat("pt-BR", {
  style: "currency",
  currency: "BRL",
});

const items = ref([]);

const readAll = async () => {
  const { data } = await supabase.from("items").select("*");
  items.value = data;
};

const destroy = async (id) => {
  const { error } = await supabase.from("items").delete().eq("id", id);
  readAll()
};

onMounted(() => {
  readAll();
});
</script>
<template>
  <div class="grid grid-cols-12 gap-6 m-auto text-gray-900">
    <ul class="flex flex-col w-full col-span-4 gap-2 p-4 shadow-md bg-gray-50 rounded-xl">
      <h2 class="w-full p-2 bg-gray-300 rounded-md">Orçamento 1</h2>
      <li v-for="item in items" class="flex flex-col w-full gap-2 p-2 border rounded-md">
        <div class="flex items-center justify-between">
          <span>Item: {{ item.item }}</span>
          <span>Preço: {{ formatter.format(item.price) }}</span>
        </div>
        <span>Descrição: {{ item.description }}</span>
        <span>Link: {{ item.link }}</span>
        <div class="flex items-center justify-end gap-4">
          <PencilSquareIcon class="w-6 cursor-pointer" />
          <TrashIcon @click="destroy(item.id)" class="w-6 cursor-pointer" />
        </div>
      </li>
    </ul>
    <ul class="flex flex-col w-full col-span-4 gap-2 p-4 shadow-md bg-gray-50 rounded-xl">
      <h2 class="w-full p-2 bg-gray-300 rounded-md">Orçamento 2</h2>
      <li v-for="item in items" class="flex flex-col w-full gap-2 p-2 border rounded-md">
        <div class="flex items-center justify-between">
          <span>Item: {{ item.item }}</span>
          <span>Preço: {{ formatter.format(item.price) }}</span>
        </div>
        <span>Descrição: {{ item.description }}</span>
        <span>Link: {{ item.link }}</span>
        <div class="flex items-center justify-end gap-4">
          <PencilSquareIcon class="w-6 cursor-pointer" />
          <TrashIcon @click="destroy(item.id)" class="w-6 cursor-pointer" />
        </div>
      </li>
    </ul>
    <ul class="flex flex-col w-full col-span-4 gap-2 p-4 shadow-md bg-gray-50 rounded-xl">
      <h2 class="w-full p-2 bg-gray-300 rounded-md">Orçamento 3</h2>
      <li v-for="item in items" class="flex flex-col w-full gap-2 p-2 border rounded-md">
        <div class="flex items-center justify-between">
          <span>Item: {{ item.item }}</span>
          <span>Preço: {{ formatter.format(item.price) }}</span>
        </div>
        <span>Descrição: {{ item.description }}</span>
        <span>Link: {{ item.link }}</span>
        <div class="flex items-center justify-end gap-4">
          <PencilSquareIcon class="w-6 cursor-pointer" />
          <TrashIcon @click="destroy(item.id)" class="w-6 cursor-pointer" />
        </div>
      </li>
    </ul>
  </div>
</template>
