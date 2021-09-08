<template>
  <vue-drag-resize :w="vw" :h="vh" :x="itemindex*(vw+40)" :isActive="isActive"
   v-on:resizing="resize" @activated="onActivated"  @deactivated="onDeactivated"
   @clicked="onClick">
    <div class="box" :style="{ width: `${vw}px`, height: `${vh}px` }">
      <input v-model="value" @change="change" id="boxinput" ref="boxinput"/>
    </div>
  </vue-drag-resize>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import VueDragResize from 'vue-drag-resize';

export default defineComponent({
  name: 'centralBox',
  props: {
    item: Object,
    index: Number,
  },
  components: {
    VueDragResize,
  },
  data() {
    return {
      vw: 100,
      vh: 100,
      value: '',
      itemindex: 0,
      isActive: false,
    };
  },
  methods: {
    resize(e:any) {
      this.vw = e.width;
      this.vh = e.height;
    },
    change(e:any) {
      console.log(e);
      const newvalue = e.target.value;
      this.value = newvalue;
      const newdata:any = this.$props.item;
      newdata.text = newvalue;
      this.$emit('changeBoxData', this.$props.index, newdata);
    },
    onActivated() {
      // eslint-disable-next-line prefer-destructuring
      const boxinput:any = this.$refs.boxinput;
      boxinput.focus();
    },
    onDeactivated() {
      this.isActive = false;
    },
    onClick() {
      this.isActive = true;
    },
  },
  mounted() {
    if (this.$props.item && this.$props.item.text) {
      this.value = this.$props.item.text;
      this.itemindex = this.$props.index ? this.$props.index : 0;
    } else {
      this.value = '-';
    }
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style   lang='less' scope>
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
  &input{
    border: none;
    width: 80%;
    text-align: center;
    background-color: transparent ;
    color: aliceblue !important;
    &:focus{
      border: none;
      box-shadow: none;
      outline: none;
    }
  }
}
</style>
