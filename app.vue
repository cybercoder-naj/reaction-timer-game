<script lang="ts" setup>
const showGreen = ref(false)
const playing = ref(false)
const diff = ref(0)

let time0 = 0

function handleClick() {
  const time = new Date().getTime()
  showGreen.value = false
  playing.value = false
  diff.value = time - time0
}

const startGame = () => {
  playing.value = true
  showGreen.value = false
  const reactionTime = (Math.random() * 5000 >> 0) + 2000
  setTimeout(() => {
    showGreen.value = true
    time0 = new Date().getTime()
  }, reactionTime)
}
</script>

<template>
  <div>
    <Box className="mx-auto" :showGreen="showGreen" :playing="playing" @clicked="handleClick" />

    <div class="mt-4 text-center">
      <button class="btn btn-primary btn-lg" :disabled="playing" @click="startGame">
        Start
      </button>

      <p v-if="diff" class="text-center mt-3">Your reaction was {{ diff }} ms.</p>
    </div>
  </div>
</template>
