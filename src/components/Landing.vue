<script setup>
import AchievmentsData from '@/assets/Data/Hoi4Achievments.json';
import CountryList from '@/assets/Data/CountryList.json';
import { ref } from 'vue';

// Reactives
const CountryChosen = ref("All Countries")

// JSON Data
const Achievments = ref(AchievmentsData);
const Countries = ref(CountryList);

// Functions
const reportIssue = () => {
  window.open('https://github.com/jakeyboi1/HOI4ABC/issues', '_blank');
};


</script>

<template>
  <div class="min-h-screen bg-[#080808] text-gray-400 font-sans antialiased flex">

    <aside class="w-72 border-r border-white/5 h-screen sticky top-0 flex flex-col bg-[#0a0a0a] z-20">
      <div class="p-8">
        <h1 class="text-white font-bold text-xl tracking-tighter flex items-center gap-2">
          HOI4 ABC
        </h1>
      </div>

      <div class="px-4 overflow-y-auto flex-1 space-y-8">
        <nav class="space-y-1">
          <p class="px-4 text-[10px] uppercase tracking-[0.2em] text-gray-600 font-bold mb-3">Countries</p>
          <button @click="CountryChosen = 'All Countries'"
            class="w-full text-left px-4 py-2.5 text-sm rounded-xl transition-all hover:bg-white/5 hover:text-white group flex items-center justify-between">
            <span class="flex items-center gap-3">
              No Filter/All Countries
            </span>
          </button>
          <button @click="CountryChosen = Country" v-for="Country in Countries" :key="Country"
            class="w-full text-left px-4 py-2.5 text-sm rounded-xl transition-all hover:bg-white/5 hover:text-white group flex items-center justify-between">
            <span class="flex items-center gap-3">
              {{ Country }}
            </span>
            <span class="text-[10px] text-gray-700 group-hover:text-gray-500 font-mono">{{ Achievments[Country].length
              }}</span>
          </button>
        </nav>
      </div>

      <div class="p-8 border-t border-white/5 text-[10px] text-gray-700 uppercase tracking-widest">
        v1.1
      </div>
    </aside>

    <main class="flex-1 min-w-0">

      <header
        class="h-20 border-b border-white/5 flex items-center justify-between px-12 bg-[#080808]/80 backdrop-blur-xl sticky top-0 z-10">
        <div class="flex items-center gap-6">
          <h2 class="text-white font-medium text-lg tracking-tight">Welcome To HOI4 Achievments By Country!
          </h2>
        </div>

        <div class="flex items-center gap-3">
          <button @click="reportIssue"
            class="px-4 py-2 bg-white/5 hover:bg-white/10 text-gray-300 text-[11px] font-bold uppercase tracking-wider rounded-xl transition-all border border-white/5 active:scale-95">
            Report Issue
          </button>
        </div>
      </header>

      <div class="p-12 max-w-[1600px] mx-auto">

        <div class="mb-20">

          <div class="flex items-center gap-4 mb-8">
            <h3 class="text-[10px] uppercase tracking-[0.4em] text-blue-500 font-black">{{ CountryChosen }}</h3>
            <div class="h-[1px] flex-1 bg-gradient-to-r from-white/10 to-transparent"></div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-5">

            <div v-if="CountryChosen != 'All Countries'" v-for="Achievment in Achievments[CountryChosen]" :key="item"
              class="group bg-[#0d0d0d] border border-white/[0.03] p-6 rounded-2xl transition-all duration-500 hover:border-white/10 hover:bg-[#111111] hover:shadow-[0_20px_40px_-20px_rgba(0,0,0,0.7)]">

              <div class="flex justify-between items-start mb-6">
                <div
                  class="w-12 h-12 bg-white/5 border border-white/5 rounded-2xl flex items-center justify-center group-hover:bg-blue-600/10 group-hover:border-blue-500/20 transition-all duration-500">
                  <svg class="w-6 h-6 text-gray-600 group-hover:text-blue-400 transition-colors" fill="none"
                    stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"
                      d="M13 10V3L4 14h7v7l9-11h-7z" />
                  </svg>
                </div>
                <span
                  class="text-[9px] font-bold tracking-widest uppercase px-2 py-1 rounded bg-white/[0.02] text-gray-600 border border-white/5 group-hover:text-gray-400 transition-colors">
                  {{ Achievment.dlc }}
                </span>
              </div>

              <div>
                <h4
                  class="text-white font-semibold text-base mb-2 tracking-tight group-hover:text-blue-100 transition-colors">
                  {{ Achievment.name }}</h4>
                <p class="text-sm text-gray-500 leading-relaxed font-light">
                  {{ Achievment.description }}
                </p>
              </div>

              <div
                class="mt-6 h-[1px] w-0 bg-gradient-to-r from-blue-600 to-transparent group-hover:w-full transition-all duration-700 opacity-40">
              </div>
            </div>


            <template v-if="CountryChosen === 'All Countries'">

              <template v-for="(achievementList, countryName) in Achievments" :key="countryName">

                <div v-for="Achievment in achievementList" :key="Achievment.name"
                  class="group bg-[#0d0d0d] border border-white/[0.03] p-6 rounded-2xl transition-all duration-500 hover:border-white/10 hover:bg-[#111111] hover:shadow-[0_20px_40px_-20px_rgba(0,0,0,0.7)]">

                  <div class="flex justify-between items-start mb-6">
                    <div
                      class="w-12 h-12 bg-white/5 border border-white/5 rounded-2xl flex items-center justify-center group-hover:bg-blue-600/10 group-hover:border-blue-500/20 transition-all duration-500">
                      <svg class="w-6 h-6 text-gray-600 group-hover:text-blue-400 transition-colors" fill="none"
                        stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"
                          d="M13 10V3L4 14h7v7l9-11h-7z" />
                      </svg>
                    </div>
                    <span
                      class="text-[9px] font-bold tracking-widest uppercase px-2 py-1 rounded bg-white/[0.02] text-gray-600 border border-white/5 group-hover:text-gray-400 transition-colors">
                      {{ Achievment.dlc }}
                    </span>
                  </div>

                  <div>
                    <h4
                      class="text-white font-semibold text-base mb-2 tracking-tight group-hover:text-blue-100 transition-colors">
                      {{ Achievment.name }}
                    </h4>
                    <p class="text-sm text-gray-500 leading-relaxed font-light">
                      {{ Achievment.description }}
                    </p>
                    <p class="mt-2 text-[10px] text-blue-500/40 uppercase tracking-widest">{{ countryName }}</p>
                  </div>

                  <div
                    class="mt-6 h-[1px] w-0 bg-gradient-to-r from-blue-600 to-transparent group-hover:w-full transition-all duration-700 opacity-40">
                  </div>
                </div>
              </template>

            </template>

          </div>
        </div>

      </div>
    </main>
  </div>
</template>

<style>
::-webkit-scrollbar {
  width: 4px;
}

::-webkit-scrollbar-track {
  background: #080808;
}

::-webkit-scrollbar-thumb {
  background: #1a1a1a;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb:hover {
  background: #252525;
}

select {
  -moz-appearance: none;
  -webkit-appearance: none;
}
</style>