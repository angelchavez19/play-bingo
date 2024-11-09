<script setup lang="ts">
import CBingo from '@/components/c-bingo.vue'
import CSelected from '@/components/c-selected.vue'
import { useBoardsStore } from '@/stores/boards'

const boards = useBoardsStore()
</script>

<template>
  <header class="Header" id="header">
    <button @click="boards.clearSelecteds">Limpiar</button>
  </header>
  <main>
    <CSelected />
    <div class="Bingos">
      <CBingo
        v-for="board in boards.boards"
        :key="board.control"
        :board="board"
        :selected="boards.selected"
      />
    </div>
    <a href="#header" class="Up">↑</a>
  </main>
</template>

<style scoped lang="sass">
@use '@/sass/utils'

.Header,
main
  padding: 1rem .3rem

.Header
  display: flex
  align-items: center
  justify-content: center
  button
    @include utils.font-1(1rem)
    background-color: red
    color: utils.$ghost-white
    border: none
    outline: none
    padding: .3rem
  button:active
    transform: scale(.8)

main
  margin-bottom: 1rem
  .Bingos
    display: flex
    align-items: center
    justify-content: center
    flex-wrap: wrap
    gap: 1rem
    width: 100%
    margin-top: 1rem
  .Up
    @include utils.font-1(1.8rem)
    position: fixed
    bottom: .7rem
    right: .7rem
    color: red
    background-color: utils.$purpureus
    color: utils.$ghost-white
    text-decoration: none
    width: 40px
    height: 40px
    border-radius: 50%
    display: flex
    align-items: center
    justify-content: center
  .Up:active
    transform: scale(.8)
</style>
