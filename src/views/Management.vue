<template>
  <div>
    <PageTitle title="Management" />
    <div class="row">
      <div class="col">
        <p>
          <font-awesome-icon :icon="['fas', 'info-circle']" /> Use this tab to
          manage robots on different sites. Please start by selecting a site.
        </p>
      </div>
    </div>
    <div class="row">
      <div class="col-md-6">
        <b-form-group id="fieldset-1" label="Site Name" label-for="input-1">
          <b-form-select
            class="form-select"
            id="input-1"
            v-model="selected"
            :options="options"
          ></b-form-select>
        </b-form-group>
      </div>
      <div class="col-md-3 mt-4">
        <div class="row">
          <div class="col-auto"><Button label="Add Robot" /></div>
          <div class="col-auto"><Button label="Add Site" /></div>
        </div>
      </div>
    </div>
    <br />
    <br />
    <h2>List of Robots</h2>
    <div class="row">
      <div class="col">
        <b-table striped hover :items="items" :fields="fields" stacked="md">
          <template #cell(actions)>
            <b-link><font-awesome-icon :icon="['fas', 'edit']" /></b-link>
            <b-link><font-awesome-icon :icon="['fas', 'trash']" /></b-link>
          </template>
        </b-table>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import PageTitle from "@/components/PageTitle.vue";
import Button from "@/components/Button.vue";
import { IconDefinition, library } from "@fortawesome/fontawesome-svg-core";
// import { name of your icon in camelCase } from "@fortawesome/free-solid-svg-icons";
// For example, I want to use fa-enveloper-open-text, then it's faEnvelopeOpenText
import {
  faInfoCircle,
  faEdit,
  faTrash,
} from "@fortawesome/free-solid-svg-icons";
// Then add it to library
library.add(
  faInfoCircle as IconDefinition,
  faEdit as IconDefinition,
  faTrash as IconDefinition
);

@Component({
  components: {
    PageTitle,
    Button,
  },
})
export default class Management extends Vue {
  @Prop() private msg!: string;
  //Dropdown properties
  selected = "Gurugram";
  options = [
    { value: null, text: "Please select an option" },
    { value: "Bhadla", text: "Bhadla" },
    { value: "New Delhi", text: "New Delhi" },
    { value: "Gurugram", text: "Gurugram" },
  ];

  //Table properties
  fields = [
    {
      label: "#",
      key: "sno",
      sortable: false,
    },
    {
      label: "Robot Name",
      key: "robot_name",
      sortable: true,
    },
    {
      label: "Robot Id",
      key: "robot_id",
      sortable: true,
    },
    {
      label: "Actions",
      key: "actions",
      sortable: false,
    },
  ];
  items = [
    {
      sno: 1,
      robot_name: "Row 1",
      robot_id: "{A08982-9098-129804}",
    },
    { sno: 2, robot_name: "Row 2", robot_id: "{B23232-2323-342234}" },
    { sno: 3, robot_name: "Row 5", robot_id: "{A29893-3434-987987}" },
    { sno: 4, robot_name: "Row 7", robot_id: "{B93433-0930-409804}" },
  ];
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
a {
  margin-right: 20px;
}
</style>
