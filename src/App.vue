<script setup>
import 'intro.js/minified/introjs.min.css';

import {
  onMounted,
  ref,
  watch,
} from 'vue';

import introJs from 'intro.js';

function startIntroWith(withOpt = 'localstorage') {
  var intro = introJs();
  const startIntro = localStorage.getItem('introduction');
  if(withOpt === 'localstorage'){
    if (!startIntro) {
    intro.oncomplete(function () {
      localStorage.setItem('introduction', true);
    }).start();
  }
  } else {
    intro.start();
  }
  

}

onMounted(() => {
  startIntroWith('localstorage');
});

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
  <div class="relative flex items-center justify-center px-0 bg-zinc-900 sm:bg-zinc-900 sm:h-screen sm:px-3">
    <div class="w-full mx-auto sm:border border-zinc-800 bg-zinc-900 sm:h-auto sm:rounded sm:shadow-xl sm:max-w-sm" data-step="1"
      data-intro="Halo! Selamat datang di aplikasi kalkulator kami yang sederhana dan praktis. Sebelum kita mulai, mari ikuti tur singkat untuk mengenal lebih jauh fitur-fitur yang tersedia.">
      <div class="flex items-center justify-between h-16 p-2 mx-auto font-bold text-center text-white">
        <span class="text-slate-200">KALKULATOR SEDERHANA</span>
        <a href="javascript:void(0)" @click="startIntroWith('btn')" data-step="2" data-intro="Menu bantuan akan membantu anda dalam memahami fitur aplikasi"
          class="text-slate-200">Guide</a>
      </div>
      <div data-step="3" data-intro="Menampilkan operasi yang anda inputkan dan menampilkan hasil inputan anda"
        class="bg-zinc-800 shadow-2xl flex justify-end items-end p-3 h-[120px]">
        <div class="flex flex-col items-end gap-2">
          <span v-if="display" id="display" class="text-3xl font-bold text-white">{{
            display
          }}</span>
          <span v-else id="display" class="text-3xl font-bold text-white">{{
              0
            }}</span>
          <span v-if="displayOutput != null" class="text-4xl font-bold text-white uppercase text-normal">= {{ displayOutput ? displayOutput.toLocaleString() : '0'
            }}</span>
        </div>
      </div>
      <div class="grid grid-cols-4 gap-4 px-5 my-5 md:gap-3">
        <button data-step="4"
          data-intro="Jika Anda hanya ingin menghapus satu angka atau operasi matematika terakhir yang dimasukkan, Anda bisa menggunakan tombol ini."
          @click="del"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center text-white font-bold bg-red-500 text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          Del
        </button>
        <button data-step="5"
          data-intro="Tombol ini berfungsi untuk menghapus semua angka yang telah dimasukkan sebelumnya, sehingga Anda bisa memulai perhitungan baru"
          @click="clear"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center text-white font-bold bg-red-500 text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          clr
        </button>
        <button data-step="6" data-intro="Tombol ini di gunakan untuk membersihkan display" @click="showToDisplay(`%`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          %
        </button>
        <button data-step="7"
          data-intro='Operator ini digunakan untuk membagi satu bilangan dengan bilangan lainnya. Contohnya, jika Anda ingin membagi 8 dengan 2, tekan tombol "8", kemudian tombol "÷", dan terakhir tombol "2", lalu tekan tombol "=".'
          @click="showToDisplay(`/`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          ÷
        </button>
        <button @click="showToDisplay(7)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          7
        </button>
        <button @click="showToDisplay(8)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          8
        </button>
        <button @click="showToDisplay(9)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          9
        </button>
        <button data-step="8"
          data-intro='Operator ini digunakan untuk mengalikan dua bilangan. Misalnya, jika Anda ingin mengalikan 4 dengan 6, tekan tombol "4", kemudian tombol "×", dan terakhir tombol "6", lalu tekan tombol "="'
          @click="showToDisplay(`*`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          x
        </button>

        <button @click="showToDisplay(4)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          4
        </button>
        <button @click="showToDisplay(5)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          5
        </button>
        <button @click="showToDisplay(6)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          6
        </button>
        <button data-step="9"
        position="top"
          data-intro='Operator ini digunakan untuk mengurangkan satu bilangan dari bilangan lainnya. Contohnya, jika Anda ingin mengurangkan 7 dari 10, tekan tombol "10", kemudian tombol "-", dan terakhir tombol "7", lalu tekan tombol "=".'
          @click="showToDisplay(`-`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          -
        </button>

        <button @click="showToDisplay(1)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          1
        </button>
        <button @click="showToDisplay(2)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          2
        </button>
        <button @click="showToDisplay(3)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          3
        </button>
        <button data-step="10"
        position="left"
          data-intro='Operator ini digunakan untuk menambahkan dua bilangan. Misalnya, jika Anda ingin menambahkan 3 dengan 5, Anda tekan tombol "3", kemudian tombol "+" dan terakhir tombol "5", '
          @click="showToDisplay(`+`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          +
        </button>

        <button @click="showToDisplay(0)"
          class="col-span-2 p-3 font-bold text-white uppercase rounded bg-zinc-800 hover:ring-1 hover:ring-slate-400 text-normal sm:text-lg aspect-auto">
          0
        </button>
        <button @click="showToDisplay(`.`)"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-zinc-800 hover:ring-1 transition-all hover:ring-slate-400  text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          .
        </button>
        <button data-step="11"
          data-intro='digunakan untuk menyelesaikan perhitungan dan mendapatkan hasil akhir dari operasi matematika yang telah Anda masukkan. Begitu Anda memasukkan angka dan melakukan operasi matematika yang diinginkan, tekan tombol "=" untuk melihat hasilnya.'
          @click="calc"
          class="h-[4.1rem] w-[4.1rem] flex items-center justify-center bg-orange-500 text-white font-bold text-normal uppercase sm:text-lg aspect-auto p-3 rounded">
          =
        </button>
      </div>
    </div>
  </div>
</template>
