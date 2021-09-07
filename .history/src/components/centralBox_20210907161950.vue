<template>
  <div class="box"
      :draggable="true"
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
