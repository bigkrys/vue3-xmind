<template>
  <div class="home">
    <dragWrap></dragWrap>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import dragWrap from '../components/dragWrap.vue';

export default defineComponent({
  name: 'Home',
  components: {
    dragWrap,
  },
});
</script>
