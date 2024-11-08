<script setup lang="ts">
import CBingo from '@/components/c-bingo.vue'
import type { BoardI } from '@/types'
import { ref } from 'vue'

const boards = ref<BoardI[]>([
  {
    control: '0000',
    b: ['7', '14', '2', '9', '5'],
    i: ['20', '25', '18', '22', '30'],
    n: ['32', '34', '44', '32'],
    g: ['45', '49', '41', '50', '47'],
    o: ['60', '70', '65', '75', '68'],
  },
  {
    control: '0001',
    b: ['3', '10', '12', '6', '15'],
    i: ['17', '24', '19', '27', '29'],
    n: ['31', '38', '34', '42'],
    g: ['46', '52', '54', '58', '59'],
    o: ['62', '66', '72', '74', '70'],
  },
  {
    control: '0002',
    b: ['1', '8', '11', '4', '13'],
    i: ['21', '23', '26', '28', '30'],
    n: ['33', '36', '40', '41'],
    g: ['48', '53', '55', '57', '60'],
    o: ['61', '64', '67', '73', '75'],
  },
  {
    control: '0003',
    b: ['5', '9', '15', '2', '14'],
    i: ['18', '22', '27', '20', '29'],
    n: ['34', '39', '31', '43'],
    g: ['47', '51', '56', '50', '58'],
    o: ['63', '68', '69', '74', '66'],
  },
  {
    control: '0004',
    b: ['2', '7', '10', '1', '12'],
    i: ['19', '26', '24', '21', '30'],
    n: ['35', '37', '43', '40'],
    g: ['44', '49', '54', '55', '59'],
    o: ['62', '65', '71', '72', '75'],
  },
  {
    control: '0005',
    b: ['4', '11', '8', '3', '6'],
    i: ['17', '25', '20', '28', '29'],
    n: ['32', '35', '34', '38'],
    g: ['46', '52', '53', '56', '57'],
    o: ['60', '63', '70', '74', '68'],
  },
])
const selected = ref<string[]>(['5', '12', '23', '34', '45', '56', '67', '72', '11', '38'])
</script>

<template>
  <main>
    <div class="Bingos">
      <CBingo v-for="board in boards" :key="board.control" :board="board" :selected="selected" />
    </div>
  </main>
</template>

<style scoped lang="sass">
main
  padding: 1rem .3rem
  .Bingos
    display: flex
    align-items: center
    justify-content: center
    flex-wrap: wrap
    gap: 1rem
    width: 100%
</style>
