<template>
  <vue-drag-resize :w="vw" :h="vh" v-on:resizing="resize" >
    <div class="box" :style="{ width: `${vw}px`, height: `${vh}px` }">
      {{msg}}
    </div>
  </vue-drag-resize>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import VueDragResize from 'vue-drag-resize';

export default defineComponent({
  name: 'centralBox',
  props: {
    msg: String,
  },
  components: {
    VueDragResize,
  },
  data() {
    return {
      vw: 200,
      vh: 200,
    };
  },
  methods: {
    resize(e:any) {
      console.log(e);
      this.vw = e.width;
      this.vh = e.height;
    },
    dragover(e:any) {
      e.preventDefault();
    },
    drop(e:any) {
      console.log('🐉drop到的点位', e);
      const getData = JSON.parse(e.dataTransfer.getData('node'));// 获取drag的数据
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
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
</style>
