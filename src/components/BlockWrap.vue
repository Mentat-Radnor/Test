<template>
  <div class="block__wrap">
    <div
      class="block__animate"
      :class="{'hidden': isHidden}"
      >
      <slot />
      <button 
        class="block__btn"
        @click="animateHidden"
      >
          <IconArrow class="block__btn-icon"/>
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

import IconArrow from './icons/IconArrow.vue';

const isHidden = ref<boolean>(false);

const animateHidden = () => {
  isHidden.value = !isHidden.value
}
</script>

<style lang="scss">
.block__wrap {
  clip-path: none !important;
}

.block__btn {
  color: hsl(0, 0%, 85%);
  background: hsl(0, 0%, 0%);
  border: hsla(0, 0%, 57%, 1);
  width: 45px;
  height: 45px;
  padding: 10px;
  cursor: pointer;
  transition: color .3s;

  position: absolute;
  top: 0;
  &:hover {
    color: hsl(0, 0%, 100%);
  }
}

.block__right .block__btn {
  left: 100%;
}

.block__left .block__btn {
  right: 100%;
  transform: rotate(180deg);
}

.block__right .block__animate {
  position: relative;
  transition: right .5s;
  right: 0;
}

.block__right .block__animate.hidden {
  right: 95%;
}

.block__left .block__animate {
  position: relative;
  transition: left .5s;
  left: 0;
}

.block__left .block__animate.hidden {
  left: 95%;
}

.block__animate.hidden .block__btn-icon {
  transform: rotate(180deg);
}
</style>