<script>
import AchievmentsData from '@/assets/Data/Hoi4Achievments.json';
import { ref } from 'vue';

export default {
  setup() {
    const CountryChosen = ref("Choose Country")
    const CountryDropdown = ref(false)
    return {
      CountryChosen, CountryDropdown
    }
  },
  data() {
    return {
      Achievments: AchievmentsData,
      Countries: CountryList
    };
  },
};


let CountryList = [
  "Any",
  "Afghanistan",
  "Argentina",
  "Australia",
  "Austria",
  "Belgium",
  "Bolivia",
  "Brazil",
  "British Raj",
  "Bulgaria",
  "Canada",
  "Chile",
  "China",
  "Chinese Soviet Republic",
  "Colombia",
  "Czechoslovakia",
  "Denmark",
  "Egypt",
  "Estonia",
  "Ethiopia",
  "Finland",
  "France",
  "Germany",
  "Greece",
  "Hungary",
  "Iceland",
  "Iran",
  "Iraq",
  "Italy",
  "Japan",
  "Luxembourg",
  "Manchukuo",
  "Mexico",
  "Netherlands",
  "Norway",
  "Philippines",
  "Poland",
  "Portugal",
  "Romania",
  "South Africa",
  "Soviet Union",
  "Spain",
  "Sweden",
  "Switzerland",
  "Turkey",
  "United Kingdom",
  "United States",
  "Yugoslavia"
]
</script>

<template>
  <main class="text-center mt-2">
    <div class="relative inline-block text-left mb-4">
      <div class="group">
        <button type="button" @click="CountryDropdown = !CountryDropdown"
          class="inline-flex justify-center items-center w-full px-4 py-2 text-sm font-medium text-white bg-gray-800 hover:bg-gray-700 focus:outline-none focus:bg-gray-700">
          {{ CountryChosen }}
          <!-- Dropdown arrow -->
          <svg class="w-4 h-4 ml-2 -mr-1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M10 12l-5-5h10l-5 5z" />
          </svg>
        </button>

        <!-- Dropdown menu -->
        <div v-if="CountryDropdown"
          class="absolute left-0 w-40 mt-1 origin-top-left bg-white divide-y divide-gray-100 rounded-md shadow-lg max-h-80 overflow-y-auto">
          <div class="py-1" v-for="Country in Countries">
            <button @click="CountryChosen = Country; CountryDropdown = !CountryDropdown;"
              class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">{{ Country }}</button>
          </div>
        </div>
      </div>
    </div>

    <div style="width: 100%;" class="text-2xl text-white text-center">Thanks for using the site! All the information was pulled from the HOI4 Wiki page, and parsed using AI, too lazy to do it myself, so if you notice something wrong click <a class="text-cyan-500 underline" href="https://github.com/jakeyboi1/HOI4ABC/issues" target="_blank">HERE</a> and open a new issue on the Github page!</div>

    <table class="table-fixed border-collapse text-white mb-2 ml-4 mt-10" style="width: 98%;">
      <colgroup>
        <col class="w-1/3" />
        <col class="w-1/3" />
        <col class="w-1/3" />
      </colgroup>
      <thead>
        <tr>
          <th class="px-4 py-2 text-left border">Name</th>
          <th class="px-4 py-2 text-left border">Description</th>
          <th class="px-4 py-2 text-left border">DLC</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="Achievment in Achievments[CountryChosen]">
          <td class="px-4 py-2 border">
            <div class="overflow-x-auto max-w-full pb-4 pt-4">
              <div class="inline-block pr-6 whitespace-nowrap">
                {{ Achievment.description }}
              </div>
            </div>
          </td>
          <td class="px-4 py-2 border">
            <div class="overflow-x-auto max-w-full pb-4 pt-4">
              <div class="inline-block pr-6 whitespace-nowrap">
                {{ Achievment.description }}
              </div>
            </div>
          </td>
          <td class="px-4 py-2 border truncate">{{ Achievment.dlc }}</td>
        </tr>
      </tbody>
    </table>
  </main>
</template>

<style scoped>
</style>