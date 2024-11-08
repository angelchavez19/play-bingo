<script setup lang="ts">
interface Props {
  num: string
  selected?: string[]
  isControl?: boolean
}
defineProps<Props>()
</script>

<template>
  <div v-if="isControl && !selected" class="BingoBody-column--control">
    <p class="BingoBody-column--control--text">Control</p>
    <p>{{ num }}</p>
  </div>
  <div v-else :class="`BingoBody-column--control${selected?.includes(num) ? '--selected' : ''}`">
    {{ num }}
  </div>
</template>

<style scoped lang="sass">
@use '@/sass/utils'

.BingoBody-column--control,
.BingoBody-column--control--selected
  @include utils.font-1(1rem)
  background-color: utils.$gunmetal
  display: flex
  align-items: center
  justify-content: center
  flex-direction: column
  color: utils.$ghost-white
  .BingoBody-column--control--text
    font-size: .5rem
.BingoBody-column--control--selected
  color: utils.$emerald
</style>
