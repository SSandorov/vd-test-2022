<template>
  <simple-card class="vd-form">
    <template #title>
      <h1>Autoverzekering vergelijken</h1>
    </template>

    <template #content>
      <Form @submit="onSubmit">
        <!-- <Field name="email" type="email" placeHolder="john@doe" :rules="validateEmail"/>
        <div class="separation-1"></div>
        <ErrorMessage name="email" /> -->

        <!-- LicensePlate -->
        <license-plate/>
        <!-- Zipcode -->
        <zip-code/>
        <!-- Housenumber -->
        <house-number/>
        <!-- Housenumber addition -->
        <house-number-addition/>
        <!-- birthdate -->
        <birth-date/>
        <!-- ClaimFree years -->
        <claim-years/>
        <!-- Kilometrage -->
        <kilometrage/>
        <div class="separation-1"></div>
        <button class="btn">Vergelijken</button>
        <!-- <div class="btn" @click="onSubmit">
            Vergelijken
        </div> -->
      </Form>
    </template>
  </simple-card>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import {
  Form,
  Field,
  ErrorMessage,
  // configure as configurationVee,
} from 'vee-validate';
import SimpleCard from './simpleCard.vue';
import LicensePlate from './inputs/licensePlate.vue';
import ZipCode from './inputs/zipCode.vue';
import HouseNumber from './inputs/houseNumber.vue';
import HouseNumberAddition from './inputs/houseNumberAddition.vue';
import BirthDate from './inputs/birthDate.vue';
import ClaimYears from './inputs/claimYears.vue';
import Kilometrage from './inputs/kilometrage.vue';

// configurationVee({
//   validateOnInput: true,
// });

@Options({
  components: {
    SimpleCard,
    LicensePlate,
    ZipCode,
    HouseNumber,
    HouseNumberAddition,
    BirthDate,
    ClaimYears,
    Kilometrage,
    Form,
    Field,
    ErrorMessage,
  },
})

export default class CarForm extends Vue {
  onSubmit(values: string): void {
    // console.log(JSON.stringify(values, null, 2));
    const exampleUrl = 'https://example.com/';
    const asString = new URLSearchParams(values).toString();
    const urlSubmission = `${exampleUrl}${asString}`;
    console.log(urlSubmission);
  }
  // validateEmail(value:string):string|boolean {
  //   // if the field is empty
  //   if (!value) {
  //     return 'This field is required';
  //   }

  //   // if the field is not a valid email
  //   const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
  //   if (!regex.test(value)) {
  //     return 'This field must be a valid email';
  //   }

  //   // All is good
  //   return true;
  // }
}
</script>

<style scoped>
    .vd-form {
        width: 330px;

        display: flex;
        justify-content: center;
        flex-direction: column;
    }

    @media only screen and (max-width: 768px) {
        .vd-form {
            width: 100%;

            /* display: flex;
            justify-content: center; */
        }
    }

    /* .btn {
        background: #0cbe3b;
        text-align: center;
        padding: 10px 10px;
        font-weight: 600;
        color: white;
        border-radius: 4px;
        cursor: pointer;
        transition: .1s ease;
    } */

    /* .btn:hover {
        background: #0ed642;
    } */
</style>
