<template>
  <div class="box">
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
  width: 50px;
  height: 20px;
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
