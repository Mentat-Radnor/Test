<template>
  <div class="main">
    <div class="blocks__row">
      <BlockToDoList 
        class="block__right"
        :list="toDoListShopping"
        @update="updateShoppingList"
      > 
        <template #title>
          SHOPPING LIST
        </template>
      </BlockToDoList>

      <BlockImage class="block__left"/>
    </div>

    <div class="blocks__row">
      <BlockText class="block__right"> 
        <template #title>
          MAMAAA OOOO
        </template>
        <template #text>
          THIS ONE IS NOT A LIST - JUST SOME PLAIN OL’ TEXT.

          IS THIS THE REAL LIFE
          IS THIS JUST FANTASY
          CAUGHT IN A LANDSIDE
          NO ESCAPE FROM REALITY

          BY THE WAY IF THERE WAS A REALLY LONG LINE, I’M PRETTY SURE AT SOME POINT IT WOULD WRAP TO THE NEXT LINE. JUST LIKE THE OTHER ELEMENTS ON THIS PAGE, THIS ONE HAS A PRE-DEFINED MAX-WIDTH 
        </template>
      </BlockText>

      <BlockToDoList 
        class="block__left"
        :list="toDoListReading"
        @update="updateReadingList"
      > 
        <template #title>
          BOOKS TO READ
        </template>
      </BlockToDoList>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import BlockToDoList from './components/BlockToDoList.vue';
import BlockText from './components/BlockText.vue';
import BlockImage from './components/BlockImage.vue';

import { ToDo } from './types';

const toDoListShopping = ref<Array<ToDo>>([
  {text:'MILK', active: false}, 
  {text: 'BREAD', active: true}, 
  {text: 'HAM', active: false},
  {text: 'Cheese', active: false},
  {text: 'Water', active: false}
]);

const toDoListReading = ref<Array<ToDo>>([
  {text:'SAPIENS BY YUVAL NOAH HARARI', active: false}, 
  {text: 'THE THEORY OF EVERYTHING BY STEPHEN HAWKINGN', active: true}, 
  {text: 'A WILD SHEEP CHASE BY HARUKI MURAKAMI', active: true},
  {text: 'CLEAN CODE BY ROBERT MARTI', active: false},
]);


const updateShoppingList = (index: number) => {
  toDoListShopping.value[index].active = !toDoListShopping.value[index].active 
}

const updateReadingList = (index: number) => {
  toDoListReading.value[index].active = !toDoListReading.value[index].active 
}
</script>

<style scoped lang="scss">
.main {
  display: flex;
  flex-direction: column;
  gap: 80px;
  background: $dark;
  width: 100%;
  min-height: 100vh;
  font-size: 20px;
  font-family: sans-serif;
  text-transform: uppercase;
  padding-top: 80px;
  padding-bottom: 20px;
  overflow-x: hidden;
}

.blocks__row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}
</style>
