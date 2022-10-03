<template>
   <span 
        class="block__img-like"
        :style="`top: ${mathRandom()}%; left: ${mathRandom()}%`"
      >
        &#10084;
      </span>
</template>

<script setup lang="ts">
const mathRandom = () => {
  const min = Math.ceil(0);
  const max = Math.floor(100);
  return Math.floor(Math.random() * (max - min) + min);
};

</script>