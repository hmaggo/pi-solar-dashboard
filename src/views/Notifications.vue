<template>
  <div>
    <PageTitle title="Notifications" />
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
    <h2>Notifications</h2>
    <div class="row">
      <div class="col">
        <b-table striped hover :items="items" :fields="fields" stacked="md">
          <template #cell(actions)>
            <b-link><font-awesome-icon :icon="['fas', 'trash']" /></b-link>
          </template>
          <template #cell(select)>
            <input
              class="form-check-input"
              type="checkbox"
              value=""
              id="flexCheckDefault"
              v-model="checkboxValue"
            />
          </template>
        </b-table>
      </div>
    </div>
    <div class="row">
      <div class="col text-end">
        <Button label="Mark as Read" />
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
export default class Notifications extends Vue {
  @Prop() private msg!: string;

  checkboxValue = false;
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
      label: "Select",
      key: "select",
      sortable: false,
    },
    {
      label: "Read/Unread",
      key: "readUnread",
      sortable: true,
    },
    {
      label: "Notification",
      key: "notification",
      sortable: true,
    },
    {
      label: "Date/Time",
      key: "dateTime",
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
      readUnread: "Unread",
      notification: "Cleaning completed for Row 1",
      dateTime: "16 May, 2021 7:15:10 PM",
    },
    {
      sno: 2,
      readUnread: "Unread",
      notification: "Battery low (10%) for Row 1",
      dateTime: "16 May, 2021 7:10:20 PM",
    },
    {
      sno: 3,
      readUnread: "Read",
      notification: "Cleaning started for Row 5",
      dateTime: "16 May, 2021 5:03:00 PM",
    },
    {
      sno: 4,
      readUnread: "Read",
      notification: "Cleaning started for Row 1",
      dateTime: "16 May, 2021 5:03:00 PM",
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
