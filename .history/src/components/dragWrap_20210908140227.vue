<template>
  <div class="drap-container" >
    <div
      class="nodeBox"
      :draggable="true"
    >
      <centralBox :item="nodeData" :index="0" @changeBoxData= "changeBoxData"></centralBox>
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
<style scoped lang='less'>
@width: 100px;
@height: 50px;

.drap-container{
  width: 80%;
  height: 80%;
}
.nodeBox {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  position: relative;
  &::before,
  &::after {
    content: "";
    border-right: 1px solid #ddd;
    height: 10px;
    width: 50%;
    position: absolute;
    top: 0;
    left: 0;
  }
  &:not(:first-child):before {
    border-top: 1px solid #ddd;
  }
  &:not(:last-child):after {
    left: 50%;
    border-right: none;
    border-top: 1px solid #ddd;
  }
  .labelName {
    width: 100px;
    height: 40px;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    border-radius: 4px;
    background-color: #66b1ff;
    margin: 10px 10px 0 10px;
    font-weight: 700;
    user-select: none;
    position: relative;
    color: #0e0e0e;
  }
  .buttonBox {
    position: absolute;
    top: 40px;
    border: 1px solid #ccc;
    background: #fff;
    border-radius: 5px;
    height: 200px;
    z-index: 999;
  }
  .showBox {
    position: absolute;
    top: 35px;
    border: 1px solid #ccc;
    background: #fff;
    height: 20px;
    width: 20px;
    border-radius: 50%;
    text-align: center;
    z-index: 99;
  }
  .buttonBox .el-button {
    margin-left: 0px !important;
  }
  .childBox {
    display: flex;
    position: relative;
    padding: 10px;
    &::after {
      content: "";
      position: absolute;
      border-left: 1px solid #ddd;
      height: 10px;
      left: 50%;
      top: 0;
    }
  }
}
#app > .nodeBox:before,
#app > .nodeBox:after {
  content: none;
}
.childBox {
  display: flex;
  position: relative;
  padding: 10px;
  &:after {
    content: "";
    position: absolute;
    border-left: 1px solid rgb(17, 15, 15);
    height: 10px;
    left:@width;
    top: @height;
  }
}
</style>
