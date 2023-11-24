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
  <div class="progress">
    <div class="progress-bar bg-info" role="progressbar" :style="{'width': this.progressValue*10+'%'}" aria-valuenow="50" aria-valuemin="0"
         aria-valuemax="100">
      {{this.progressValue}}/10
    </div>
  </div>
</template>

<style>

</style>
