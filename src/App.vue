<script setup>
  import { ref, computed } from 'vue'
  
  const thrown = ref([]);

  const count = computed(() => {
    let countObj = {
      1: 0,
      2: 0,
      3: 0,
      4: 0,
      5: 0,
      6: 0
    };

    thrown.value.forEach(die => {
      countObj[die]++
    })

    return countObj;
  });


  const throwDice = () => {
    thrown.value = [];

    for (let d=0; d<8; d++){
      let dice = Math.floor(Math.random() * 6) + 1
      thrown.value.push(dice)
    }
  }
</script>

<template>
  <button
    @click="throwDice"
    class="mt-4 mb-4 px-4 py-2 bg-blue-600 text-slate-50 text-lg rounded-lg">Throw Dice
  </button>
  <table>
    <thead class="border-b-4 solid border-black">
      <tr>
        <th class="border-r-2 solid border-gray-400 px-2">Number</th>
        <th class="px-2">Count</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(dice, index) in count" :key="index">
        <td class="text-center border-r-2 solid border-gray-400 px-2">{{ index }}</td>
        <td class="text-center px-2">{{ dice }}</td>
      </tr>
    </tbody>
  </table>
</template>
