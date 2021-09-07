<template>
  <div class="box" @mousedown="mousedown" @mousemove="mousemove" @mouseup="mouseup">
    {{msg}}
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'centralBox',
  props: {
    msg: String,
  },
  components: {
  },
  data() {
    return {
    };
  },
  methods: {
    mousedown(e:any) {
      console.log('mousedown', e);
    },
    mousemove(e:any) {
      console.log('mousemove', e);
    },
    mouseup(e:any) {
      console.log('🐉drop到的点位', e);
    },
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box{
  width: 100px;
  height: 50px;
  border-radius: 8px;
  background-color: brown;
  color: aliceblue;
  display: inline-flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
</style>
