<template>
    <p>House Number Addition</p>
    <Field
    name="house-number-addition"
    type="text"
    :rules="validHouseNumberAddition"
    oninput="this.value = this.value.replace(/[^0-9A-Z]/i, '').replace(/(\..*)\./i, '$1')"
    />
    <div class="separation-1"></div>
    <ErrorMessage name="house-number-addition"/>
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

export default class HouseNumberAddition extends Vue {
  validHouseNumberAddition(value:string):string|boolean {
    // if the field is not a valid licence plate
    const regex = /^[0-9A-Z]/i;
    if (!regex.test(value)) {
      return 'This field must contain numbers and/or letters';
    }
    // All is good
    return true;
  }
}
</script>
