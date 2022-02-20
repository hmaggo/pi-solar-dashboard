<template>
  <div>
    <div class="row mt-4">
      <div class="col">
        <h1>{{ title }}</h1>
      </div>
      <div class="col text-end">
        <b-nav-item-dropdown class="userName" text="Himanshu Maggo" right>
          <b-dropdown-item href="#">Security</b-dropdown-item>
          <b-dropdown-item href="#">Logout</b-dropdown-item>
        </b-nav-item-dropdown>
      </div>
    </div>
    <hr />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class PageTitle extends Vue {
  @Prop() title!: string;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
li {
  list-style: none;
}
.userName a {
  color: black;
}
</style>
