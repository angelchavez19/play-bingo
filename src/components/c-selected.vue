<script setup lang="ts">
import { useBoardsStore } from '@/stores/boards'

const boards = useBoardsStore()
</script>

<template>
  <div class="Selecteds">
    <div
      v-for="num in 75"
      :key="num"
      @click="boards.addSelected(`${num}`)"
      :class="`Selecteds-ball${boards.selected.includes(`${num}`) ? '--included' : ''}`"
    >
      <p>{{ num }}</p>
    </div>
  </div>
</template>

<style scoped lang="sass">
@use '@/sass/utils'

.Selecteds
  display: flex
  flex-wrap: wrap
  align-items: center
  justify-content: center
  gap: .2rem
  .Selecteds-ball,
  .Selecteds-ball--included
    @include utils.font-1(1.2rem)
    background-color: utils.$davys-gray
    color: utils.$ghost-white
    width: 40px
    height: 40px
    border-radius: 50%
    display: flex
    align-items: center
    justify-items: center
    cursor: pointer
    p
      width: 100%
      text-align: center
  .Selecteds-ball--included
    background-color: utils.$emerald
    color: utils.$davys-gray
  .Selecteds-ball:active,
  .Selecteds-ball--included:active
    transform: scale(.8)
</style>
