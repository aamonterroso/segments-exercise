<template>
  <div>
    <div v-for="(item, index) in computerList" :key="index">
      <ComputerItem :spaceLabel="item.space"/>
    </div>
  </div>
</template>

<script>
  import ComputerItem from "./ComputerItem.vue";
  export default {
    name: 'SegmentLayout',
    components: {
      ComputerItem,
    },
    props: {
      computerList: {
        type: Array,
        required: true
      },
      segment: {
        type: Number,
        default: 1
      },
    },
    data() {
      return {
      }
    },
    methods: {
      buildSegmentMatrix() {
        
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>