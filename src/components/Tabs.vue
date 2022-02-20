<template>
  <div>
    <div class="multiTabs">
      <b-tabs pills>
        <div v-for="item in computedData" :key="item.index">
          <b-tab :title="item.value" @click="tabClick(item)"></b-tab>
        </div>
      </b-tabs>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Tabs extends Vue {
  @Prop() private data!: any;

  get computedData() {
    return this.data !== null && this.data !== undefined
      ? this.data
      : this.testData;
  }

  testData = [
    {
      index: 1,
      value: "Real-time",
    },
    {
      index: 2,
      value: "Monthly",
    },
    {
      index: 3,
      value: "Yearly",
    },
  ];

  tabClick(event: any) {
    console.log("tabClick", event);
    this.$emit("tabClicked", event);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.multiTabs .tabs {
  background: #f6f6f6;
  border-radius: 20px;
  width: max-content;
}

.multiTabs {
  li {
    a {
      border-radius: 20px !important;
      margin-top: 5px;
      margin-bottom: 5px;
      margin-left: 5px;
      margin-right: 5px;
      color: black;
      padding-top: 0.2rem;
      padding-right: 1rem;
      padding-bottom: 0.2rem;
      padding-left: 1rem;
      font-size: 0.7rem;
    }
    .active {
      background-color: #ffdf01 !important;
      color: black !important;
    }
  }
}

.borderRadius {
  color: red;
  border-radius: 20px;
  margin-top: 5px;
  margin-bottom: 5px;
  margin-left: 5px;
}

.bigValue {
  display: flex;
}
.valueLabel {
  font-weight: 600;
}
</style>
