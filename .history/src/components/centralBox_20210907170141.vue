<template>
  <div class="box"
      :draggable="true"
      @dragstart="dragstart($event)"
      @dragover="dragover($event)"
      @drop="drop($event)"
      @dragend="dragend($event)"
      >
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
    dragstart(e:any) {
      console.log(e);
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
