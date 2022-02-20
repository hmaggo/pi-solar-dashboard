<template>
  <div>
    <div class="row">
      <div class="col">
        <h2>Savings</h2>
      </div>
      <div class="col alignRight">
        <Tabs @tabClicked="overviewTabClicked($event)" :data="savingsTabData" />
      </div>
    </div>

    <div class="row mt-3">
      <div class="col">
        <span class="valueLabel">Water Saved</span>
        <div class="bigValue">
          <h1 class="display-3">90 L</h1>
        </div>
      </div>
      <div class="col">
        <span class="valueLabel">Money Savings</span>
        <div class="bigValue">
          <h1 class="display-3">₹10,000</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import Tabs from "@/components/Tabs.vue";

@Component({
  components: {
    Tabs,
  },
})
export default class Savings extends Vue {
  @Prop() private msg!: string;

  //Site overview tabs
  savingsTabData = [
    {
      index: 1,
      value: "Monthly",
    },
    {
      index: 2,
      value: "Yearly",
    },
  ];
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
.alignRight {
  text-align: -webkit-right;
}
</style>
