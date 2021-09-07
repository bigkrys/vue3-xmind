<template>
  <vue-drag-resize :w="vw" :h="vh" v-on:resizing="resize" >
    <div class="box" :style="{ width: `${vw}px`, height: `${vh}px` }">
      <input v-model="value" @change="change"/>
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
    };
  },
  methods: {
    resize(e:any) {
      this.vw = e.width;
      this.vh = e.height;
    },
    change(e:any) {
      console.log(e);
    },
  },
  mounted() {
    if (this.$props.item && this.$props.item.name) {
      this.value = this.$props.item.name;
    } else {
      this.value = '-';
    }
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  lang="scss" scoped>
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
    background-color: transparent;
    color: aliceblue;
  }
}
</style>
