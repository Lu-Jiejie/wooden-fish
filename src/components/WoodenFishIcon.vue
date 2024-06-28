<script setup lang="ts">
import { BASIC_SYMBOLS, WOODEN_FISH_RAW_MATRIX as rawMatrix } from '../constant'

const matrix: string[][] = []
for (let row = 0; row < rawMatrix.length; row += 2) {
  const curRow = []
  for (let col = 0; col < rawMatrix[0].length; col++) {
    curRow.push(BASIC_SYMBOLS[rawMatrix[row][col]][rawMatrix[row + 1][col]])
  }
  matrix.push(curRow)
}
</script>

<template>
  <Text v-for="(row, i) in matrix" :key="i">
    <Text v-for="(col, j) in row" :key="j" color="white">
      {{ col }}
    </Text>
  </Text>
</template>
