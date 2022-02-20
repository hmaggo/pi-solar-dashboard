<template>
  <div>
    <PageTitle title="Service Requests" />
    <div class="row">
      <div class="col">
        <p>
          <font-awesome-icon :icon="['fas', 'info-circle']" /> Use this tab to
          read notifications. Please start by selecting a site.
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
    </div>
    <br />
    <br />
    <h2>Submitted Requests</h2>
    <div class="row">
      <div class="col">
        <b-table striped hover :items="items" :fields="fields" stacked="md">
        </b-table>
      </div>
    </div>
    <hr class="mt-4" />
    <h2>Submit Service Request</h2>
    <div class="row mt-3">
      <div class="col">
        <textarea
          class="form-control"
          id="exampleFormControlTextarea1"
          rows="4"
        ></textarea>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col text-end">
        <Button label="Submit" />
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
export default class ServiceRequests extends Vue {
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
      label: "Request",
      key: "request",
      sortable: true,
    },
    {
      label: "Submit Date/Time",
      key: "dateTime",
      sortable: true,
    },
    {
      label: "Status",
      key: "status",
      sortable: true,
    },
  ];
  items = [
    {
      sno: 1,
      request: "Request to replace the motor on row 1.",
      dateTime: "17 May, 2021 7:15:10 PM",
      status: "New",
    },
    {
      sno: 2,
      request:
        "Row 5 robot has stopped working. Please send an engineer to evaluate and rectify.",
      dateTime: "14 May, 2021 5:10:00 PM",
      status: "In-progress",
    },
    {
      sno: 3,
      request:
        "Row 3 robot brush needs replacement. Please send the spare parts.",
      dateTime: "10 April, 2021 10:01:55 AM",
      status: "Completed",
    },
  ];
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
a {
  margin-right: 20px;
}
</style>
