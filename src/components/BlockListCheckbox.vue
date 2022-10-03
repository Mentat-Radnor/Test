<template>
  <label class="block__checkbox-wrap">
    <input 
      :checked="todo.active"
      type="checkbox"
      class="block__checkbox"
      @click="handler__click"
    >
    <span class="block__checkbox-text">
      {{ todo.text }}
    </span>
  </label> 
</template>

<script setup lang="ts">
import { ToDo } from '../types';

defineProps<{todo: ToDo}>();

const emits = defineEmits<{(e: 'check'): void}>();

const handler__click = () => {
  emits('check')
}

</script>

<style lang="scss">
.block__checkbox {
  display: none;
}

.block__checkbox-text {
  cursor: pointer;
}

.block__checkbox:checked ~ .block__checkbox-text{
  text-decoration: line-through;
}
</style>