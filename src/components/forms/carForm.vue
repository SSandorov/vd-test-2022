<template>
  <simple-card class="vd-form">
    <template #title>Autoverzekering vergelijken</template>

    <template #content>
      <Form @submit="onSubmit">
        <!-- <Field name="email" type="email" placeHolder="john@doe" :rules="validateEmail"/>
        <div class="separation-1"></div>
        <ErrorMessage name="email" /> -->

        <!-- LicensePlate -->
        <licence-plate/>
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
import { Form, Field, ErrorMessage } from 'vee-validate';
import SimpleCard from './simpleCard.vue';
import LicencePlate from './inputs/licencePlate.vue';
import ZipCode from './inputs/zipCode.vue';
import HouseNumber from './inputs/houseNumber.vue';
import HouseNumberAddition from './inputs/houseNumberAddition.vue';
import BirthDate from './inputs/birthDate.vue';
import ClaimYears from './inputs/claimYears.vue';
import Kilometrage from './inputs/kilometrage.vue';

@Options({
  components: {
    SimpleCard,
    LicencePlate,
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
    console.log(JSON.stringify(values, null, 2));
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
    }

    @media only screen and (max-width: 768px) {
        .vd-form {
            width: 100%;
        }
    }

    .btn {
        background: #0cbe3b;
        text-align: center;
        padding: 10px 10px;
        font-weight: 600;
        color: white;
        border-radius: 4px;
        cursor: pointer;
        transition: .1s ease;
    }

    .btn:hover {
        background: #0ed642;
    }
</style>
