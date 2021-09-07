<template>
  <div class="home">
    <centralBox></centralBox>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import centralBox from "@/components/centralBox.vue"

export default defineComponent({
  name: 'Home',
  components: {
    centralBox,
  },
});
</script>
