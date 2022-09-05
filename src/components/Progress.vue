<template>
  <div class="progress">
    <div class="progress-bar bg-info" role="progressbar" :style="{width:progress+'%'}" aria-valuenow="50"
      aria-valuemin="0" aria-valuemax="100">
      {{ itemCount }}/10
    </div>
  </div>
</template>
<script>
import { eventBus } from "../main"
export default {
  data() {
    return {
      itemCount: 0,
      progress: 0
    }
  },

  created() {
    eventBus.$on("progressBarUpdated", (productListCount) => {
      this.itemCount = productListCount
      this.progress = productListCount * 10
    });
  }
}
</script>