<template>
  <div id="app">
    <!-- <NavBar /> -->
    <div class="container-fluid">
      <div class="row d-lg-none">
        <div class="col text-center mt-4">
          <a class="navbar-brand" href="#">
            <img src="@/assets/atmus-logo.png" alt="Logo" />
          </a>
        </div>
      </div>
      <div class="row">
        <div class="col-md-2">
          <SideBar />
        </div>

        <main role="main" class="col-lg-10 noLeftPadding customMarginBottom">
          <router-view />
        </main>
        <BottomBar class="sidebar-bottom d-lg-none" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import SideBar from "@/components/SideBar.vue";
import BottomBar from "@/components/BottomBar.vue";

@Component({
  components: {
    SideBar,
    BottomBar,
  },
})
export default class App extends Vue {
  @Prop() title!: string;
}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Montserrat");
html,
body {
  font-family: "Monserrat", sans-serif !important;
}

.noLeftPadding {
  padding-right: 3rem !important;
  padding-left: 3rem !important;
}

@media (max-width: 992px) {
  .customMarginBottom {
    margin-bottom: 6rem;
  }
}
</style>
