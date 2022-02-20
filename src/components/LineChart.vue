<script lang="ts">
import { Line } from "vue-chartjs";
import { Component, Mixins, Prop, Vue } from "vue-property-decorator";

@Component
export default class LineChart extends Mixins(Line) {
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
