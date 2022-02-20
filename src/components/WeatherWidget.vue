<template>
  <div>
    <div class="padding">
      <div class="col">
        <div class="card">
          <img
            class=""
            src="https://i.imgur.com/a9sHoeY.jpg"
            alt="Card image cap"
          />
          <div class="card-img-overlay" style="height: 110px">
            <h3 class="card-title text-white m-b-0 dl">Gurugram</h3>
            <br />
            <small class="card-text text-white font-light"
              >Saturday, 16th May 2021</small
            >
          </div>
          <div class="card-body weather-small">
            <div class="row">
              <div class="col-8 b-r align-self-center">
                <div class="d-flex">
                  <div class="display-6 text-info">
                    <i class="mdi mdi-weather-pouring"></i>
                  </div>
                  <div class="m-l-20">
                    <h1 class="font-light text-info m-b-0">
                      32<sup class="supClass">0</sup>
                    </h1>
                    <small>Rainy day</small>
                  </div>
                </div>
              </div>
              <div class="col-4 text-center">
                <h1 class="font-light m-b-0">
                  25<sup class="supClass">0</sup>
                </h1>
                <small>Tonight</small>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class WeatherWidget extends Vue {
  @Prop() private msg!: string;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import url("https://cdnjs.cloudflare.com/ajax/libs/MaterialDesign-Webfont/3.6.95/css/materialdesignicons.css");
body {
  background-color: #000000;
}

.card-no-border .card {
  border-color: #d7dfe3;
  border-radius: 4px;
  -webkit-box-shadow: 0px 5px 20px rgba(0, 0, 0, 0.05);
  box-shadow: 0px 5px 20px rgba(0, 0, 0, 0.05);
}

.card-img-overlay {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  padding: 1.25rem;
}

html body .dl {
  display: inline-block;
}

.text-white {
  color: #ffffff !important;
}

.font-light {
  font-weight: 300;
}

.card-text:last-child {
  margin-bottom: 0;
}

.card-body {
  -ms-flex: 1 1 auto;
  flex: 1 1 auto;
  padding: 1.25rem;
}

.b-r {
  border-right: 1px solid rgba(120, 130, 140, 0.13);
}

.text-info {
  color: #1e88e5 !important;
}

.display-6 {
  font-size: 36px;
}

.mdi {
  display: inline-block;
  font-family: "weathericons";
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.m-l-20 {
  margin-left: 20px;
}

.m-b-0 {
  margin-bottom: 0px;
}

small {
  font-size: 80%;
  font-weight: 400;
}

.supClass {
  top: -1.9em !important;
  font-size: 0.3em !important;
}
</style>
