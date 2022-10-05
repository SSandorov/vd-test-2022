<template>
  <div class="kilometrage-container">
    <label for="kilometrage">Kilometrage</label>
    <Field
      id="kilometrage"
      class="field"
      v-model="selected"
      name="kilometrage"
      as="select"
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
        v-for="type in kilometres"
        :key="type.text"
        :value="type.value">{{type.text}}
      </option>
    </Field>
    <div class="separation-1"></div>
    <ErrorMessage name="kilometrage"/>
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

export default class Kilometrage extends Vue {
    selected = '7501 t/m 10000 KM';

    kilometres = [
      { text: '0 t/m 7500 KM', value: '0 t/m 7500 KM' },
      { text: '7501 t/m 10000 KM', value: '7501 t/m 10000 KM' },
      { text: '10001 t/m 12000 KM', value: '10001 t/m 12000 KM' },
      { text: '12001 t/m 15000 KM', value: '12001 t/m 15000 KM' },
      { text: '15001 t/m 20000 KM', value: '15001 t/m 20000 KM' },
      { text: '20001 t/m 25000 KM', value: '20001 t/m 25000 KM' },
      { text: '25001 t/m 30000 KM', value: '25001 t/m 30000 KM' },
      { text: '30001 t/m 90000 KM', value: '30001 t/m 90000 KM' },
    ];
}
</script>

<style scoped>
  .kilometrage-container {
    width: 100%;
    display: flex;
    flex-direction: column;
  }
</style>
