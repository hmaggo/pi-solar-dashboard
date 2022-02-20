<template>
  <div>
    <!-- for Desktop -->
    <nav class="sidebar d-none d-lg-block">
      <a class="navbar-brand" href="#">
        <img src="../assets/atmus-logo.png" alt="Logo" />
      </a>
      <div class="sidebar-sticky">
        <ul class="nav flex-column">
          <!-- tachometer-alt -->
          <li class="nav-item">
            <a
              class="nav-link"
              href="#"
              @click="routeToDashboard"
              :class="{ active: selectedValue === 'Dashboard' }"
            >
              <span
                ><font-awesome-icon :icon="['fas', 'tachometer-alt']"
              /></span>
              Dashboard
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              href="#"
              @click="routeToNotifications"
              :class="{ active: selectedValue === 'Notifications' }"
            >
              <span><font-awesome-icon :icon="['fas', 'bell']" /></span>
              Notifications <span class="badge bg-secondary">4</span>
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              href="#"
              @click="routeToManagement"
              :class="{ active: selectedValue === 'Management' }"
            >
              <span><font-awesome-icon :icon="['fas', 'tasks']" /></span>
              Management
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              href="#"
              @click="routeToServiceRequests"
              :class="{ active: selectedValue === 'ServiceRequests' }"
            >
              <span><font-awesome-icon :icon="['fas', 'cog']" /></span>
              Service Requests
            </a>
          </li>
        </ul>
      </div>
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
export default class SideBar extends Vue {
  @Prop() private msg!: string;
  text: any;
  showSideBar = true;
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
<style scoped lang="scss">
.sidebar {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  z-index: 100; /* Behind the navbar */
  padding: 10px 0 0; /* Height of navbar */
  box-shadow: inset -1px 0 0 rgba(0, 0, 0, 0.1);
  background-color: #ffdf01;
}

.sidebar-sticky {
  position: relative;
  top: 0;
  height: calc(100vh - 48px);
  padding-top: 0.5rem;
  overflow-x: hidden;
  overflow-y: auto; /* Scrollable contents if viewport is shorter than content. */
}

@supports ((position: -webkit-sticky) or (position: sticky)) {
  .sidebar-sticky {
    position: -webkit-sticky;
    position: sticky;
  }
}

.sidebar .nav {
  padding: 48px 0 0; /* Height of navbar */
  //   align-content: center;
  //   align-items: center;
}

.sidebar .nav-link {
  font-weight: 500;
  color: #333;
}

.sidebar .nav-link svg {
  margin-right: 10px;
}

.sidebar .nav-link.active {
  font-weight: bolder;
}

.sidebar-heading {
  font-size: 0.75rem;
  text-transform: uppercase;
}

.sidebar .navbar-brand {
  margin-left: 1rem;
}

.sidebar li {
  margin-bottom: 20px;
}
</style>
