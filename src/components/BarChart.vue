<script lang="ts">
import { Bar } from "vue-chartjs";
import { Component, Mixins, Prop, Vue } from "vue-property-decorator";

@Component
export default class BarChart extends Mixins(Bar) {
  @Prop() labels!: Array<string>;
  @Prop() datasets!: Array<any>;
  mounted() {
    this.renderChart(
      {
        labels: this.labels,
        datasets: this.datasets,
      },
      { responsive: true, maintainAspectRatio: false }
    );
  }
}
</script>
