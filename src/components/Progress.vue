<script>
import {eventBus} from "../main";

export default {
  name: "Progress",
  data(){
    return{
      progressValue:0
    }
  },
  created() {
    eventBus.$on("productListLength", (length) => {
      this.progressValue = length;
    });
  }
}
</script>

<template>
  <div class="progress" v-if="progressValue>0">
    <div class="progress-bar bg-info" role="progressbar" :style="{'width': this.progressValue*10+'%'}" aria-valuenow="0" aria-valuemin="0"
         aria-valuemax="120">
      {{this.progressValue}}/12
    </div>
  </div>
</template>

<style>

</style>
