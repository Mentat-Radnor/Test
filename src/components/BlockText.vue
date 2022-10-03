<template>
  <BlockWrap>
    <div class="block" v-bind="$attrs">
      <h2 class="block__title">
        <slot name="title" />
      </h2>
      <p>
        <slot name="text" />
      </p>
    </div>
  </BlockWrap>
</template>

<script setup lang="ts">
import BlockWrap from './BlockWrap.vue';
</script>