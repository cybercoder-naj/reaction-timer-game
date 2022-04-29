<script lang="ts" setup>
interface BoxProps {
  className: string;
  showGreen: boolean;
  playing: boolean
}

const props = defineProps<BoxProps>();

const emit = defineEmits(['clicked']);

const handleClick = () => {
  if (props.showGreen) {
    emit('clicked');
  }
}
</script>

<template>
  <div 
    :class="`${className} reaction-box ${showGreen && playing && 'bg-green'}`"
    @click="handleClick"
  >
    <p v-if="playing">Click here as soon as the box turns green.</p>
    <p v-else>Press the start button.</p>
  </div>
</template>

<style scoped>
.reaction-box {
  width: 500px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px dashed green;
  color: green;
  background-color: #eeeeee;
  cursor: pointer;
}

.bg-green {
  background-color: green;
}
</style>
