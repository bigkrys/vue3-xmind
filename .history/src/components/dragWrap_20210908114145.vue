<template>
  <div class="drap-container" >
    <div
      class="labelName"
      :draggable="true"
    >
      {{ nodeData.text }}
    </div>
    <div class="childBox" v-if="nodeData.children.length>0">
      <template v-for="(item,index) in nodeData.children" :key="item.id">
        <centralBox :item="item" :index="index" @changeBoxData= "changeBoxData"></centralBox>
      </template>
    </div>
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
      nodeData: {
        id: 0,
        text: '中心主题',
        children: [
          {
            id: 1,
            text: '分支主题1',
            children: [],
          },
          {
            id: 2,
            text: '分支主题2',
            children: [],
          },
        ],
      },
    };
  },
  methods: {
    changeBoxData(index:number, data:any) {
      console.log('fater', index, data);
      this.myArray[index] = data;
    },
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
