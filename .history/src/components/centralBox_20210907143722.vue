<template>
  <div class="hello">
    <draggable v-model="myArray" tag="transition-group" item-key="id">
      <template #item="{element}">
        <div> {{element.name}} </div>
      </template>
    </draggable>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import draggable from 'vuedraggable';

export default defineComponent({
  name: 'centralBox',
  props: {
    msg: String,
  },
  components: {
    draggable,
  },
  data() {
    return {
      drag: false,
      myArray: [
        {
          text: 'hello',
        },
      ],
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
