<template>
    <p>Birth Date</p>
    <Field
    id="birth-date"
    name="birth-date"
    type="text"
    placeholder="DD-MM-YYYY"
    :rules="validBirthDate"
    :onkeyup="getInput"
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
  input = 0;

  validBirthDate(value:string):string|boolean {
  // if the field is empty
    if (!value) {
      return 'This field is required';
    }

    if (!moment(value, 'DD-MM-YYYY', true).isValid()) {
      return 'This field must contain a valid date';
    }

    const actualYear = moment().format('YYYY');
    const birthDateYear = value.slice(6);

    const transform1 = Number(actualYear);
    const transform2 = Number(birthDateYear);

    // for dates older or equal to 100 years
    if (transform1 - transform2 >= 100) {
      return 'You must be under 100 years old';
    }

    // if the field is not a valid date
    // const regex = /^[0-9]{2}[-]{1}[0-9]{2}[-]{1}[0-9]{4}/g;
    // if (!regex.test(value)) {
    //   return 'This field must have the following format DD-MM-YYYY';
    // }
    // All is good
    // We add the year of birth to the property input
    this.input = transform2;
    // we store the year of the birthDate for the claimYears calculation
    localStorage.setItem('actualYear', actualYear);
    localStorage.setItem('birthdate', birthDateYear);
    return true;
  }

  getInput():number {
    // console.log(this.input);
    return this.input;
  }

  // storeInput(char:string):string {
  //   if (this.validBirthDate()) {
  //   }
  // }
}
</script>
