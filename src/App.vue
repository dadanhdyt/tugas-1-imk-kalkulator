<script setup>
import { ref, watch } from "vue";

const display = ref(``);
const displayOutput = ref(null);

function del() {
  display.value = display.value.slice(0, -1);
}

function showToDisplay(i) {
  display.value += `${i}`;
}
function calc() {
  displayOutput.value = eval(`${display.value}`);
}
function clear() {
  display.value = '';
  displayOutput.value = null;
}
</script>

<template>
  <div class="bg-gray-900 flex px-3 sm:px-0 items-center justify-center h-screen">
    <div class="sm:max-w-sm rounded overflow-hidden shadow-xl w-full mx-auto bg-gray-700">
      <div class="text-white text-center mx-auto p-2 font-bold">KALKULATOR SEDERHANA</div>
      <div class="bg-slate-500 flex justify-end items-end p-5 h-[100px]">
        <div class="flex flex-col items-end gap-2">
          <span v-if="display" id="display" class="font-bold text-white text-2xl">{{
            display
          }}</span>
          <span v-else id="display" class="font-bold text-white text-2xl">{{
            0
          }}</span>
          <span v-if="displayOutput != null" class="font-bold text-white text-normal uppercase sm:text-lg"
            >= {{ displayOutput }}</span
          >
        </div>
      </div>
      <div class="grid gap-4 my-5 px-5 grid-cols-4">
        <button
          @click="del"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center text-white font-bold bg-red-500 text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          Del
        </button>
        <button
          @click="clear"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center text-white font-bold bg-red-500 text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          clr
        </button>
        <button
          @click="showToDisplay(`%`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          %
        </button>
        <button
          @click="showToDisplay(`/`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          /
        </button>
        <button
          @click="showToDisplay(7)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          7
        </button>
        <button
          @click="showToDisplay(8)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          8
        </button>
        <button
          @click="showToDisplay(9)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          9
        </button>
        <button
          @click="showToDisplay(`*`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          *
        </button>

        <button
          @click="showToDisplay(4)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          4
        </button>
        <button
          @click="showToDisplay(5)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          5
        </button>
        <button
          @click="showToDisplay(6)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          6
        </button>
        <button
          @click="showToDisplay(`-`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          -
        </button>

        <button
          @click="showToDisplay(1)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          1
        </button>
        <button
          @click="showToDisplay(2)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          2
        </button>
        <button
          @click="showToDisplay(3)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          3
        </button>
        <button
          @click="showToDisplay(`+`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          +
        </button>

        <button
          @click="showToDisplay(0)"
          class=" bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full col-span-2"
        >
          0
        </button>
        <button
          @click="showToDisplay(`.`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-gray-600 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          .
        </button>
        <button
          @click="calc"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded-full"
        >
          =
        </button>
      </div>
    </div>
  </div>
</template>
