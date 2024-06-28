<script lang="ts" setup>
import process from 'node:process'
import Vaultify from 'vaultify'

let lastUpdate = 0
const updateInterval = 2000

const vault = new Vaultify({
  name: 'WoodenFish',
})

const counter = ref(vault.get<number>('counter', 0))

onKeyData([' ', 'Enter'], () => {
  counter.value++
  if (Date.now() - lastUpdate >= updateInterval) {
    vault.set('counter', counter.value)
    lastUpdate = Date.now()
  }
})

process.on('exit', () => {
  vault.set('counter', counter.value)
})
</script>

<template>
  <Box
    :padding="0"
    :margin="0"
    width="100%"
    max-width="70"
    justify-content="center"
    align-items="center"
    flex-direction="column"
    border-color="yellowBright"
    border-style="round"
  >
    <Newline />

    <Text>
      功德：<Text bold>
        {{ counter }}
      </Text>
    </Text>

    <Newline />

    <GongDePlus />

    <WoodenFishIcon />

    <Newline />

    <Text color="gray">
      按下
      <Text underline>
        {{ 'Space' }}
      </Text>
      或
      <Text underline>
        {{ 'Enter' }}
      </Text>
      积攒功德
    </Text>
  </Box>
</template>
