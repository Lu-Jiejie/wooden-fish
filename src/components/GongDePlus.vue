<script setup lang="ts">
const props = withDefaults(defineProps<{
  max?: number
  interval?: number
  eventKey?: string[]
}>(), {
  max: 5,
  interval: 100,
  eventKey: () => [' ', 'Enter'],
})
const states = ref(Array(props.max).fill(false))
const reverseStates = computed(() => states.value.slice().reverse())
const statesLength = states.value.length

function startTransition() {
  for (let i = 0; i < statesLength; i++) {
    setTimeout(() => {
      states.value[i] = true
      setTimeout(() => {
        states.value[i] = false
      }, props.interval)
    }, props.interval * i)
  }
}

onKeyData(props.eventKey as any, () => {
  startTransition()
})
</script>

<template>
  <Box v-for="(state, index) in reverseStates" :key="index">
    <Text v-if="state" color="gray">
      功德+1
    </Text>
    <Text v-else>
      {{ ' ' }}
    </Text>
  </Box>
</template>
