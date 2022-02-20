<template>
  <div class="dashboard">
    <PageTitle title="Dashboard" />
    <div class="row">
      <div class="col">
        <p>
          <font-awesome-icon :icon="['fas', 'info-circle']" /> Please select a
          site and robot to view details.
        </p>
      </div>
    </div>
    <!-- Dropdowns -->
    <div class="row">
      <div class="col-md-6">
        <b-form-group id="fieldset-1" label="Site Name" label-for="input-1">
          <b-form-select
            class="form-select"
            id="input-1"
            v-model="selectedSite"
            :options="optionsSite"
          ></b-form-select>
        </b-form-group>
      </div>
      <div class="col mt-md-0 mt-3">
        <b-form-group id="fieldset-1" label="Robot Name" label-for="input-1">
          <b-form-select
            class="form-select"
            id="input-1"
            v-model="selectedRobot"
            :options="optionsRobot"
          ></b-form-select>
        </b-form-group>
      </div>
    </div>
    <hr class="mt-4" />
    <!-- Overview-->
    <div class="row mt-4">
      <div class="col">
        <h2>Robot Statistics</h2>
      </div>
      <div class="col alignRight">
        <Tabs @tabClicked="overviewTabClicked($event)" />
      </div>
    </div>
    <!--Robot Statisitcs - Real-time data -->
    <div class="row mt-4" v-if="showRealTime">
      <div class="col">
        <span class="valueLabel">Cleaning Status</span>
        <div class="bigValue">
          <h1 class="display-6">In-progress</h1>
        </div>
      </div>
      <div class="col">
        <span class="valueLabel">Battery</span>
        <div class="bigValue">
          <h1 class="display-3">90</h1>
          <div class="littleValue mb-2 mb-md-3">%</div>
        </div>
      </div>
      <div class="col mt-3 mt-md-0">
        <span class="valueLabel">Distance from base</span>
        <div class="bigValue">
          <h1 class="display-3">2</h1>
          <div class="littleValue mb-2 mb-md-3">m</div>
        </div>
      </div>
      <div class="col mt-3 mt-md-0">
        <span class="valueLabel">Current Speed</span>
        <div class="bigValue">
          <h1 class="display-3">10</h1>
          <div class="littleValue mb-2 mb-md-3">m/s</div>
        </div>
      </div>
      <!-- Stop and send to base buttons -->
      <div class="col d-none d-md-block">
        <div class="row">
          <div class="col">
            <Button label="Stop Robot" />
          </div>
        </div>
        <div class="row mt-4">
          <div class="col">
            <Button label="Send to base" />
          </div>
        </div>
      </div>
    </div>
    <div class="row d-md-none" v-if="showRealTime">
      <!-- Stop and send to base buttons -->
      <div class="col">
        <div class="row">
          <div class="col">
            <Button label="Stop Robot" />
          </div>
        </div>
        <div class="row mt-4">
          <div class="col">
            <Button label="Send to base" />
          </div>
        </div>
      </div>
    </div>
    <!--Robot Statisitcs - Weekly data -->
    <div class="row mt-4" v-if="showWeekly">
      <div class="row">
        <div class="col-md-6">
          <h3>Count of cleanings (May)</h3>
          <BarChart
            :labels="monthlyCleaningsLabels"
            :datasets="monthlyCleaningsDataset"
          />
        </div>
        <div class="col-md-6">
          <h3>Battery Usage (May)</h3>
          <LineChart
            :labels="monthlyCleaningsLabels"
            :datasets="monthlyBatteryDataset"
          />
        </div>
      </div>
    </div>
    <hr class="mt-4" />
    <!-- Schedule Information -->
    <div class="row">
      <div class="col-md-6 pe-md-4">
        <div class="row">
          <div class="col">
            <h2>Schedule Information</h2>
          </div>
        </div>
        <div class="row">
          <div class="col">
            <b-card
              overlay
              :img-src="require('../assets/time-background-2.jpg')"
              img-alt="Card Image"
              text-variant="white"
            >
              <div class="row">
                <div class="col text-end">
                  <b-link style="color: #ffff">
                    <font-awesome-icon :icon="['fas', 'pencil-alt']" />
                  </b-link>
                </div>
              </div>
              <div class="row mt-lg-4">
                <div class="col">
                  <div class="bigValue">
                    <h1 class="display-2">09:00</h1>
                    <div class="littleValue mb-2 mb-md-3">AM</div>
                  </div>
                </div>
              </div>
              <div class="row mt-lg-4">
                <div class="col"><h4>Mon, Tue, Wed, Thu, Fri</h4></div>
              </div>
            </b-card>
          </div>
        </div>
      </div>
      <hr class="mt-4 d-md-none" />
      <div class="col-md-6 ps-md-4">
        <div class="row">
          <div class="col">
            <h2>Site Overview</h2>
          </div>
          <div class="col alignRight">
            <Tabs
              @tabClicked="overviewTabClicked($event)"
              :data="siteTabData"
            />
          </div>
        </div>
        <div class="row mt-4">
          <div class="col">
            <span class="valueLabel">Installation Size</span>
            <div class="bigValue">
              <h1 class="display-3">5</h1>
              <div class="littleValue mb-2 mb-md-3">MW</div>
            </div>
          </div>
          <div class="col">
            <span class="valueLabel">Energy Generated</span>
            <div class="bigValue">
              <h1 class="display-3">12</h1>
              <div class="littleValue mb-2 mb-md-3">MWH</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <hr class="mt-4" />
    <!-- Site Overview -->
    <div class="row mt-4 mb-4">
      <div class="col-md-6 pe-md-4">
        <Savings />
      </div>
      <hr class="mt-4 d-md-none" />
      <!--2nd column -->
      <div class="col-md-6 ps-md-4">
        <WeatherWidget />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import WeatherWidget from "@/components/WeatherWidget.vue";
import Savings from "@/components/Savings.vue";
import Tabs from "@/components/Tabs.vue";
import PageTitle from "@/components/PageTitle.vue";
import Button from "@/components/Button.vue";
import BarChart from "@/components/BarChart.vue";
import LineChart from "@/components/LineChart.vue";
// this is must have
import { IconDefinition, library } from "@fortawesome/fontawesome-svg-core";
// import { name of your icon in camelCase } from "@fortawesome/free-solid-svg-icons";
// For example, I want to use fa-enveloper-open-text, then it's faEnvelopeOpenText
import { faPencilAlt } from "@fortawesome/free-solid-svg-icons";
// Then add it to library
library.add(faPencilAlt as IconDefinition);

@Component({
  components: {
    WeatherWidget,
    Savings,
    Tabs,
    PageTitle,
    Button,
    BarChart,
    LineChart,
  },
})
export default class Dashboard extends Vue {
  showRealTime = true;
  showWeekly = false;

  //Dropdown properties
  selectedSite = "Gurugram";
  optionsSite = [
    { value: null, text: "Please select an option" },
    { value: "Bhadla", text: "Bhadla" },
    { value: "New Delhi", text: "New Delhi" },
    { value: "Gurugram", text: "Gurugram" },
  ];

  //Dropdown properties
  selectedRobot = "Row 1";
  optionsRobot = [
    { value: null, text: "Please select an option" },
    { value: "Row 1", text: "Row 1" },
    { value: "Row 2", text: "Row 2" },
    { value: "Row 5", text: "Row 5" },
    { value: "Row 7", text: "Row 7" },
  ];

  overviewTabClicked(value: any) {
    console.log("overviewTabClicked", value, value.index === 2);
    if (value.index === 1) {
      this.showRealTime = true;
      this.showWeekly = false;
    } else if (value.index === 2) {
      this.showRealTime = false;
      this.showWeekly = true;
    }
  }

  //Site overview tabs
  siteTabData = [
    {
      index: 1,
      value: "Monthly",
    },
    {
      index: 2,
      value: "Yearly",
    },
  ];

  monthlyCleaningsLabels = ["Week 1", "Week 2", "Week 3", "Week 4"];
  monthlyCleaningsDataset = [
    {
      label: "Count of cleanings",
      backgroundColor: "#f87979",
      data: [5, 4, 7, 1],
    },
  ];

  monthlyBatteryDataset = [
    {
      label: "Average Battery run-time (Hrs)",
      data: [6, 6, 5, 6],
      fill: false,
    },
  ];
}
</script>
<style lang="scss" scoped>
.bigValue {
  display: flex;
}
.littleValue {
  align-self: flex-end;
  font-size: 24px;
}
.valueLabel {
  font-weight: 600;
}
.verticalLine {
  border-left: thick solid #ff0000;
}
.leftSeparator {
  border-left: thin solid lightgray;
  margin-left: 1rem;
}
.alignRight {
  text-align: -webkit-right;
}
</style>
