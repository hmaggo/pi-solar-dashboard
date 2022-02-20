<template>
  <div class="hello">
    <b-button pill variant="outline-secondary">{{ label }}</b-button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Button extends Vue {
  @Prop() label!: string;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.btn-outline-secondary {
  color: #000 !important;
  border-color: #ffdf01 !important;
  border-width: medium !important;
  &:hover {
    background-color: #ffdf01 !important;
  }
}

@media (max-width: 576px) {
  .btn {
    width: -webkit-fill-available !important;
  }
}
</style>
