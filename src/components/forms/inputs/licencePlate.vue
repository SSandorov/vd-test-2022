<template>
  <p>Licence Plate</p>
  <Field
    style="text-transform: uppercase;"
    name="licence-plate"
    type="text"
    :rules="validLicence"
    oninput="this.value=this.value.replace('-','').replace(' ', '');
    this.value=this.value.toUpperCase()"
    onpaste="return false"
    autocomplete="off"
    required
  />
  <div class="separation-1"></div>
  <ErrorMessage name="licence-plate"/>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import { Field, ErrorMessage } from 'vee-validate';

@Options({
  components: {
    Field,
    ErrorMessage,
  },
})

export default class LicencePlate extends Vue {
  validLicence(value:string):string|boolean {
    // if the field is empty
    if (!value) {
      return 'This field is required';
    }
    // if the field is not a valid licence plate
    const regex = /^[A-Z0-9]{6}$/i;
    if (!regex.test(value)) {
      return 'This field must be a valid licence plate XXXXXX';
    }
    // All is good
    return true;
  }
}
</script>
