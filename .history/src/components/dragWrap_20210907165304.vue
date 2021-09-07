<template>
  <div class="drap-container" >
    <template v-for="item in myArray" :key="item.id">
      <centralBox :msg="item.name"></centralBox>
    </template>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
// import draggable from 'vuedraggable';
import centralBox from './centralBox.vue';

export default defineComponent({
  name: 'dragWrap',
  props: {
    msg: String,
  },
  components: {
    // draggable,
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
.drap-container{
  width: 80%;
  height: 80%;
}
</style>
