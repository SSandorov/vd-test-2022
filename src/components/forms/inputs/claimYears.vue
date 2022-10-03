<template>
    <p>Claim Free Years</p>
    <Field
        v-model="selected"
        name="claim-years"
        as="select"
        :onclick="nClaimYears"
        required
    >
        <!-- <option value="0 t/m 7500 KM">0 t/m 7500 KM</option>
        <option value="" selected>7501 t/m 10000 KM</option>
        <option value="10001 t/m 12000 KM">10001 t/m 12000 KM</option>
        <option value="12001 t/m 15000 KM">12001 t/m 15000 KM</option>
        <option value="15001 t/m 20000 KM">15001 t/m 20000 KM</option>
        <option value="20001 t/m 25000 KM">20001 t/m 25000 KM</option>
        <option value="25001 t/m 30000 KM">25001 t/m 30000 KM</option>
        <option value="30001 t/m 90000 KM">30001 t/m 90000 KM</option> -->
        <option
        v-for="year in years"
        :key="year.text"
        :value="year.value">{{year.text}}</option>
    </Field>
    <div class="separation-1"></div>
    <ErrorMessage name="kilometrage"/>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import { Field, ErrorMessage } from 'vee-validate';
import BirthDate from './birthDate.vue';

@Options({
  components: {
    Field,
    ErrorMessage,
    BirthDate,
  },
})

export default class ClaimYears extends Vue {
    selected = 0;

    claimYears = {};

    nClaimYears():any {
      // const birth = new BirthDate();
      // const inputBirthDate2 = birth.getInput();
      const inputBirthDate2 = Number(localStorage.getItem('birthdate'));
      // console.log(inputBirthDate2);
      const inputActualYear = Number(localStorage.getItem('actualYear'));

      const range = inputActualYear - inputBirthDate2 - 18;
      console.log(range);

      Object.assign(this.claimYears, { text: range, value: range });
    }

    years = [
      { text: -5, value: -5 },
      { text: -4, value: -4 },
      { text: -3, value: -3 },
      { text: -2, value: -2 },
      { text: -1, value: -1 },
      { text: 0, value: 0 },
      this.claimYears,
    ];
}
// let inputBirthDate = localStorage.getItem('birthdate');
</script>
