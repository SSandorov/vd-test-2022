<template>
  <div class="house-add-container">
    <label for="house-number-addition">House Number Addition</label>
    <Field
      id="house-number-addition"
      class="field"
      name="house-number-addition"
      type="text"
      :rules="validHouseNumberAddition"
      oninput="this.value = this.value.replace(/[^0-9A-Z]/i, '').replace(/(\..*)\./i, '$1')"
    />
    <div class="separation-1"></div>
    <ErrorMessage name="house-number-addition"/>
  </div>
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

<style scoped>
  .house-add-container {
    width: 150px;
    display: flex;
    flex-direction: column;
  }

  /* .field {
    width: 100%;
    border: 1px red solid;
  } */
</style>
