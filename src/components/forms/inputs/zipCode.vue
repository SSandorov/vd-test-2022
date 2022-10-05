<template>
  <div class="zip-code-container">
    <label for="zip-code">Zip Code</label>
    <Field
      id="zip-code"
      class="field"
      style="text-transform: uppercase;"
      name="zip-code"
      type="text"
      :rules="validZipCode"
      oninput="this.value=this.value.replace(' ', '');
      this.value=this.value.toUpperCase()"
      required
    />
    <div class="separation-1"></div>
    <ErrorMessage name="zip-code"/>
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

export default class ZipCode extends Vue {
  validZipCode(value:string):string|boolean {
    // if the field is empty
    if (!value) {
      return 'This field is required';
    }
    // if the field is not a valid Zip Code
    // 9 years ago, do not know if it still applies
    // var rege = /^[1-9][0-9]{3} ?(?!sa|sd|ss)[a-z]{2}$/i;
    const regex = /^[1-9][0-9]{3}[A-Z]{2}$/i;
    if (!regex.test(value)) {
      return 'This field must be a valid zip code XXXXAA';
    }
    // All is good
    return true;
  }
}
</script>

<style scoped>
  .zip-code-container {
    width: 100%;
    display: flex;
    flex-direction: column;
  }
</style>
