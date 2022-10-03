<template>
  <BlockWrap>
    <div class="block block__img" v-bind="$attrs">
      <div class="block__img-wrap">
        <img src="../assets/KITTY.jpeg" alt="cat">
        <BlockLikeIcon 
          v-for="like in likeCount"
          :key="`like-${like}`"
        />
      </div>
      <button @click="addLike">Like</button>
    </div>
  </BlockWrap>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import BlockWrap from './BlockWrap.vue';
import BlockLikeIcon from './BlockLikeIcon.vue';

const likeCount = ref<number>(0);

const addLike = () => {
  likeCount.value += 1
}
</script>

<style lang="scss">
.block__img {
  position: relative;
  display: flex;
  flex-direction: column;
}

.block__img-wrap {
  position: relative;
}

.block__img-like {
  position: absolute;
  color: hsl(0, 100%, 50%);
}
</style>