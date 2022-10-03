<template>
    <p>House Number</p>
    <Field
    name="house-number"
    type="text"
    :rules="validHouseNumber"
    oninput="this.value = this.value.replace(/[^0-9]/g, '').replace(/(\..*)\./g, '$1')"
    required
    />
    <div class="separation-1"></div>
    <ErrorMessage name="house-number"/>
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

export default class HouseNumber extends Vue {
  validHouseNumber(value:string):string|boolean {
  // if the field is empty
    if (!value) {
      return 'This field is required';
    }
    // if the field is not a valid house number
    const regex = /^[0-9]/g;
    if (!regex.test(value)) {
      return 'This field must contain only numbers';
    }
    // All is good
    return true;
  }
}
</script>
