<script setup lang="ts">
import type { BoardI } from '@/types'
import CBingoCell from './c-bingo-cell.vue'

interface Props {
  board: BoardI
  selected: string[]
}

defineProps<Props>()
const header = ['b', 'i', 'n', 'g', 'o']
</script>

<template>
  <div class="BingoContainer">
    <div class="BingoHeader">
      <div v-for="head in header" :key="head">{{ head }}</div>
    </div>
    <div class="BingoBody">
      <div class="BingoBody-column">
        <CBingoCell v-for="num in board.b" :key="num" :num="num" :selected="selected" />
      </div>
      <div class="BingoBody-column">
        <CBingoCell v-for="num in board.i" :key="num" :num="num" :selected="selected" />
      </div>
      <div class="BingoBody-column">
        <CBingoCell :num="board.n[0]" :selected="selected" />
        <CBingoCell :num="board.n[1]" :selected="selected" />
        <CBingoCell :num="board.control" :isControl="true" />
        <CBingoCell :num="board.n[2]" :selected="selected" />
        <CBingoCell :num="board.n[3]" :selected="selected" />
      </div>
      <div class="BingoBody-column">
        <CBingoCell v-for="num in board.g" :key="num" :num="num" :selected="selected" />
      </div>
      <div class="BingoBody-column">
        <CBingoCell v-for="num in board.o" :key="num" :num="num" :selected="selected" />
      </div>
    </div>
  </div>
</template>

<style scoped lang="sass">
@use '@/sass/utils'

.BingoContainer
  width: 300px
  background-color: utils.$davys-gray
  border-radius: 10px
  padding: .5rem
  .BingoHeader
    display: grid
    grid-template-columns: repeat(5, 1fr)
    margin-bottom: .5rem
    div
      @include utils.font-1(2rem)
      text-transform: uppercase
      text-align: center
      color: utils.$ghost-white
  .BingoBody
    display: grid
    grid-template-columns: repeat(5, 1fr)
    gap: .1rem
    height: 230px
    .BingoBody-column
      display: grid
      grid-template-rows: repeat(5, 1fr)
      gap: .1rem
</style>
