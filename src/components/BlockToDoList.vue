<template>
  <BlockWrap>
    <div class="block" v-bind="$attrs">
      <h2 class="block__title">
        <slot name="title" /> [
        {{ activeToDo }} / {{ list.length }}
        ]
      </h2>
      <ul class="block__list">
        <li
          v-for="(todo, index) in list"
          :key="`${todo}-${index}`"
          class="block__list-li"
        >
          <BlockListCheckbox 
            :todo="todo"
            @check="updateTodo(index)"
          />
        </li>
      </ul>

    </div>
  </BlockWrap>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import BlockWrap from './BlockWrap.vue';
import BlockListCheckbox from './BlockListCheckbox.vue';
interface ToDo {
  text: string,
  active: boolean,
}

const props = defineProps<{list: Array<ToDo>}>();

const emits = defineEmits<{(e: 'update', index: number ): void}>();

const activeToDo = computed<number>(() => props.list.filter((element: ToDo) => element.active === true ).length)

const updateTodo = (index : number) => {
  emits('update', index)
}
</script>

<style lang="scss">
.block {
  max-width: 600px;
  width: fit-content;
  padding: 40px 30px;
  background: hsla(0, 0%, 57%, 1);
}

.block__right {
  clip-path: polygon(0% 0%, 100% 0, 100% calc(100% - 40px), calc(100% - 40px) 100%, 0% 100%);
}

.block__left {
  clip-path: polygon(0 0, 100% 0%, 100% 100%, 40px 100%, 0 calc(100% - 40px));
}

.block__title {
  font-size: 30px;
  font-weight: 400;
}
</style>