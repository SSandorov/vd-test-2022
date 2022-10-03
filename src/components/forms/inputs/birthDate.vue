<template>
    <p>Birth Date</p>
    <Field
    name="birth-date"
    type="text"
    placeholder="DD-MM-YYYY"
    :rules="validBirthDate"
    oninput="this.value = this.value.replace(/[^0-9-]/g, '').replace(/(\..*)\./g, '$1')"
    required
    />
    <div class="separation-1"></div>
    <ErrorMessage name="birth-date"/>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import { Field, ErrorMessage } from 'vee-validate';
import moment from 'moment';

@Options({
  components: {
    Field,
    ErrorMessage,
  },
})

export default class BirthDate extends Vue {
  validBirthDate(value:string):string|boolean {
  // if the field is empty
    if (!value) {
      return 'This field is required';
    }
    // if the field is not a valid date
    // const regex = /^[0-9]{2}[-]{1}[0-9]{2}[-]{1}[0-9]{4}/g;
    // if (!regex.test(value)) {
    //   return 'This field must have the following format DD-MM-YYYY';
    // }
    if (!moment(value, 'DD-MM-YYYY').isValid()) {
      return 'This field must contain a valid date';
    }
    // All is good
    return true;
  }
}
</script>
