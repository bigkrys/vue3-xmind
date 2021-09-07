<template>
  <div class="hello">
    <draggable v-model="myArray" tag="transition-group" item-key="id">
      <template #item="{element}">
        <centralBox :msg="element.name"></centralBox>
      </template>
    </draggable>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import draggable from 'vuedraggable';
import centralBox from './centralBox.vue';


export default defineComponent({
  name: 'dragWrap',
  props: {
    msg: String,
  },
  components: {
    draggable,
    centralBox,
  },
  data() {
    return {
      drag: true,
      myArray: [
        {
          name: 'hello',
          id: 1,
        },
        {
          name: 'world',
          id: 2,
        },
      ],
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
