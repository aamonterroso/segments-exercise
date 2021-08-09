<template>
  <div class="segmentForm">
    <h1>{{ title }}</h1>
    <form ref="segmentForm">
      <div class="segmentForm__section">
        <label htmlFor="computerQty" style="form-label">How many computers? </label>
        <input type="number" class="inputText" v-model.number="computerQty" id="computerQty" />
        <label htmlFor="rowSegment" style="form-label">row segment: </label>
        <input type="number" class="inputText" v-model.number="rowSegment" id="rowSegment" />
      </div>
      <div class="segmentForm__section inputFields">
        <div v-for="(item, index) in computerList" :key="index" class="inputSpace">
          <label :htmlFor="'spaceInput'+index" style="form-label">Comp.{{index+1}}:</label>
          <input v-model.number="item.space"
            type="number" 
            style="inputText" 
            :name="'spaceInput'+index" 
            placeholder="GB"
          />
          <div class="inputDivider" v-if="showSpacer(index)"/>
        </div>
      </div>
      <button type="button" v-on:click="showLayout = true" >Build Layout</button>
      <button type="button" v-on:click="resetForm()" >Reset</button>
      <div class="segmentForm__section computerLayout" v-show="showLayout">
        <SegmentLayout :computerList="computerList" :segment="rowSegment" />
      </div>
    </form>
  </div>
</template>

<script>
import SegmentLayout from "./SegmentLayout.vue";
export default {
  name: 'segmentForm',
  components: {
    SegmentLayout
  },
  props: {
    title: String
  },
  data() {
    return {
      rowSegment: 1,
      computerQty: 1,
      computerList: [],
      showLayout: false,
    }
  },
  created () {
    this.initComputerList();
  },
  watch: {
    computerQty(newVal, oldVal) {
      if(newVal > oldVal) {
        const id = (this.computerList.length+1).toString(10);
        this.computerList.push({
          'id': id,
          'space' : null
        });
      } else {
        this.computerList.splice(newVal, this.computerList.length-1);
      }
    }
  },
  methods: {
    initComputerList() {
      this.computerList = new Array(this.computerQty)
        .fill(null)
        .map((el, index) => ({
          'id': `${index+1}`,
          'space' : null
        }));
    },
    showSpacer(index) {
      return (index+1) % this.rowSegment === 0;
    },
    resetForm() {
      this.computerQty = 1;
      this.rowSegment = 1;
      this.showLayout = false;
      this.computerList[0] = {'id':"1", 'space':null}
    }
  },
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.segmentForm {
  width: 720px;
  margin: 0 auto;
}
.segmentForm__section {
  width: 100%;
}
.inputFields {
  padding-top: 1rem;
  display: block;
  width: 45%;
  margin: 0 auto;
}
.inputSpace {
  margin: 0 auto;
  width: 100%;
}
.inputText {
  margin-right: 1rem;
}
.inputDivider {
  margin-bottom: 1rem;
}
.computerLayout {
  width: 80%;
  padding: 1rem 1rem;
  margin: 0 auto;
}
</style>
