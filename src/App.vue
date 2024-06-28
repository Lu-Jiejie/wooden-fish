<script lang="ts" setup>
const counter = ref(0)

onKeyData([' ', 'Enter'], () => {
  counter.value++
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
