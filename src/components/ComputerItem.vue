<template>
  <div class="computerItem">
    <div class="computerItem__iconWrapper">
      <img src="../assets/computer.png" class="computerImg"/>
      <h5 v-if="spaceLabel > 0"> {{spaceLabel}} GB</h5>
      <h5 v-else> -- GB</h5>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'ComputerItem',
    props: {
      spaceLabel: {
        type: Number
      },
    }
  }
</script>

<style scoped>
.computerItem {
  float: left;
  height: 6.5rem;
}
.computerItem__iconWrapper {
  height: 5rem;
  width: 7rem;
}
.computerImg {
  max-height: 100%;
  max-width: 100%;
}
h5 {
  margin-top: 0;
}
</style>