<template>
  <label for="cliam-years">Claim Free Years</label>
  <Field
    id="claim-years"
    class="field"
    v-model="selected"
    name="claim-years"
    as="select"
    :onfocus="nClaimYears"
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
    v-for="(year, index) in years"
    :key="index"
    :value="String(year)"
    >{{year}}</option>
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
    selected = '0';

    years: number[] = [-5, -4, -3, -2, -1, 0];

    // claimYears = {};

    nClaimYears():void {
      // const birth = new BirthDate();
      // const inputBirthDate2 = birth.getInput();
      const inputBirthDate = Number(localStorage.getItem('birthdate'));
      // console.log(inputBirthDate2);
      const inputActualYear = Number(localStorage.getItem('actualYear'));

      if (inputBirthDate < inputActualYear - 100) {
        this.years = [];
      } else {
        const range = inputActualYear - inputBirthDate - 18;

        const defaultYears: number[] = [-5, -4, -3, -2, -1, 0];

        const rangeClaimYears = [...Array(range + 1).keys()];
        // console.log(rangeClaimYears);

        const iteration = (val:number) => {
        // Object.assign(this.claimYears, { text: val, value: val });
        // console.log(val);
          if (val === 0) {
            this.years = defaultYears;
          } else {
            defaultYears.push(val);
          }
        };

        rangeClaimYears.forEach(iteration);

        this.years = defaultYears;
      }
      // for (let i = 0; i <= rangeClaimYears.length; i += 1) {
      // Object.assign(this.claimYears, { text: i, value: i });
      // this.claimYears['text'] = i;
      // this.claimYears['value'] = i;
      // }
    }
}
// let inputBirthDate = localStorage.getItem('birthdate');
</script>
