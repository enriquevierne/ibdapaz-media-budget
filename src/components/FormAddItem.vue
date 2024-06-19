<script setup>
import { ref } from "vue";
import { supabase } from "../lib/supabaseClient";

const newObj = ref({ item: null, price: null, description: null, link: null });

const submit = async () => {
  const { data, error } = await supabase
    .from("items")
    .insert([{ item: newObj.value.item, price: newObj.value.price, description: newObj.value.description, link: newObj.value.link }])
    .select();
    
};
</script>

<template>
  <form @submit.prevent="submit" class="grid grid-cols-12 gap-2 p-4 m-auto shadow-md bg-gray-50 rounded-xl text-slate-100">
    <div class="flex items-center w-full col-span-3 gap-2 p-2 bg-gray-300 border-2 border-gray-300 rounded-md focus-within:border-gray-600">
      <label class="p-1 text-sm font-semibold rounded text-slate-900" for="Item">Item</label>
      <input class="w-full bg-transparent outline-none text-slate-900" type="text" v-model="newObj.item" />
    </div>

    <div class="flex items-center w-full col-span-2 gap-2 p-2 bg-gray-300 border-2 border-gray-300 rounded-md focus-within:border-gray-600">
      <label class="p-1 text-sm font-semibold rounded text-slate-900" for="jack">Preço</label>
      <input class="w-full bg-transparent outline-none text-slate-900" type="number" v-model="newObj.price" />
    </div>

    <div class="flex items-center w-full col-span-3 gap-2 p-2 bg-gray-300 border-2 border-gray-300 rounded-md focus-within:border-gray-600">
      <label class="p-1 text-sm font-semibold rounded text-slate-900" for="john">Descrição</label>
      <input class="w-full bg-transparent outline-none text-slate-900" type="text" v-model="newObj.description" />
    </div>

    <div class="flex items-center w-full col-span-4 gap-2 p-2 bg-gray-300 border-2 border-gray-300 rounded-md focus-within:border-gray-600">
      <label class="p-1 text-sm font-semibold rounded text-slate-900" for="mike">Link</label>
      <input class="w-full bg-transparent outline-none text-slate-900" type="text" v-model="newObj.link" />
    </div>
    <button class="col-span-2 col-start-11 p-2 text-sm font-bold tracking-wide uppercase bg-gray-800 rounded-md text-slate-100">adicionar</button>
  </form>
</template>
