<template>
  <div>
    <!-- For mobile -->
    <nav class="">
      <a
        @click="routeToDashboard"
        :class="{ active: selectedValue === 'Dashboard' }"
        ><font-awesome-icon :icon="['fas', 'tachometer-alt']"
      /></a>
      <a
        @click="routeToNotifications"
        :class="{ active: selectedValue === 'Notifications' }"
      >
        <font-awesome-icon :icon="['fas', 'bell']" /> &nbsp;
        <span class="badgeCustom bg-secondary">4</span>
      </a>

      <a
        @click="routeToManagement"
        :class="{ active: selectedValue === 'Management' }"
        ><font-awesome-icon :icon="['fas', 'tasks']"
      /></a>
      <a
        @click="routeToServiceRequests"
        :class="{ active: selectedValue === 'ServiceRequests' }"
        ><font-awesome-icon :icon="['fas', 'cog']"
      /></a>
    </nav>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
// this is must have
import { IconDefinition, library } from "@fortawesome/fontawesome-svg-core";
// import { name of your icon in camelCase } from "@fortawesome/free-solid-svg-icons";
// For example, I want to use fa-enveloper-open-text, then it's faEnvelopeOpenText
import {
  faEnvelopeOpenText,
  faTachometerAlt,
  faBell,
  faCog,
  faTasks,
} from "@fortawesome/free-solid-svg-icons";
// Then add it to library
library.add(
  faEnvelopeOpenText as IconDefinition,
  faBell as IconDefinition,
  faTachometerAlt as IconDefinition,
  faCog as IconDefinition,
  faTasks as IconDefinition
);

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  selectedValue = "Dashboard";
  routeToManagement() {
    this.selectedValue = "Management";
    this.$router.push({ name: "Management", params: { userId: "123" } });
  }

  routeToDashboard() {
    this.selectedValue = "Dashboard";
    this.$router.push({ name: "Dashboard", params: { userId: "123" } });
  }

  routeToNotifications() {
    this.selectedValue = "Notifications";
    this.$router.push({ name: "Notifications", params: { userId: "123" } });
  }

  routeToServiceRequests() {
    this.selectedValue = "ServiceRequests";
    this.$router.push({ name: "ServiceRequests", params: { userId: "123" } });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.sidebar-bottom {
  background-color: #ffdf01;
  overflow: hidden;
  position: fixed;
  bottom: 0;
  width: 100%;
  z-index: 1000;
  display: flex;
  justify-content: center;
}
/* Style the links inside the navigation bar */
.sidebar-bottom a {
  font-weight: 500;
  color: #333;
  float: left;
  display: block;
  text-align: center;
  padding: 15px 23px;
  text-decoration: none;
  font-size: 25px;
}

/* Change the color of links on hover */
.sidebar-bottom a:hover {
  background-color: #04aa6d;
  color: black;
}

/* Add a color to the active/current link */
.sidebar-bottom a.active {
  background-color: #04aa6d;
  color: white;
}

.badgeCustom {
  top: 0;
  right: 0;
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: 700;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: super;
  background-color: #777;
  border-radius: 10px;
}
</style>
