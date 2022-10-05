<template>
  <div class="license-container">
    <label for="license-plate">License Plate</label>
    <Field
      id="license-plate"
      class="field"
      style="text-transform: uppercase;"
      name="license-plate"
      type="text"
      :rules="validLicense"
      oninput="this.value=this.value.replace('-','').replace(' ', '');
      this.value=this.value.toUpperCase()"
      onpaste="return false"
      autocomplete="off"
      required
    />
    <div class="separation-1"></div>
    <p class="" v-if="showCarInfo()">{{carInfo}}</p>
    <ErrorMessage name="license-plate"/>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import { Field, ErrorMessage } from 'vee-validate';

// export interface VehicleData {
//   brand: string,
//   dateAdmission: number
// }

@Options({
  components: {
    Field,
    ErrorMessage,
  },
})

export default class LicensePlate extends Vue {
  carInfo = '';

  warningMessage = '';

  showCarInfo():boolean {
    if (this.carInfo.length === 0) {
      return false;
    }
    return true;
  }

  validLicense(value:string):string|boolean {
    // if the field is empty
    if (!value) {
      this.carInfo = '';
      return 'This field is required';
    }
    // if the field is not a valid licence plate
    const regex = /^[A-Z0-9]{6}$/i;
    if (!regex.test(value)) {
      this.carInfo = '';
      return 'This field must be a valid license plate XXXXXX';
    }

    // if (!this.rdwApi(value)) {
    //   this.carInfo = '';
    //   this.warningMessage = 'This is not a valid license plate';
    //   return this.warningMessage;
    // }

    this.warningMessage = '';
    // All is good
    return true;
  }

  rdwApi(value:string):string {
    const urlRDW = 'https://opendata.rdw.nl/resource/m9d7-ebf2.json';
    const getVehicle = async () => {
      // const resp = await fetch(`${urlRDW}?kenteken=${value}`);

      // if (!resp.ok) {
      //   return 'Not a valid licence plate';
      // }
      // // eslint-disable-next-line camelcase
      // const [{ merk, datum_eerste_toelating }] = await resp.json();
      // const yearAdm = datum_eerste_toelating.slice(0, 4);

      // // eslint-disable-next-line arrow-body-style
      // const capitalizeBrand = (val:string) => {
      //   return val.charAt(0).toUpperCase() + val.slice(1).toLowerCase();
      // };
      // const brand = capitalizeBrand(merk);
      // // const vehStr = JSON.stringify(data);
      // // console.log(Object.values(vehStr));
      // const carInfo = `${brand} ${yearAdm}`;
      // console.log(carInfo);
      // return carInfo;
      fetch(`${urlRDW}?kenteken=${value}`)
        .then((resp) => resp.json())
        // eslint-disable-next-line camelcase
        .then(([{ merk, datum_eerste_toelating }]) => {
          const yearAdm = datum_eerste_toelating.slice(0, 4);
          // eslint-disable-next-line arrow-body-style
          const capitalizeBrand = (val:string) => {
            return val.charAt(0).toUpperCase() + val.slice(1).toLowerCase();
          };
          const brand = capitalizeBrand(merk);
          this.warningMessage = '';
          this.carInfo = `${brand} ${yearAdm}`;
          // console.log(this.carInfo);
        })
        .catch((resp) => {
          if (resp) {
            // reset value of carInfo to show text when it is not a correct license plate
            // covers the issue of putting a correct license but it is not yours, so the
            // value can be reset to start again
            this.carInfo = '';
          }
          return resp;
        });
    };
    getVehicle();
    return this.carInfo;
  }
}
</script>

<style scoped>
  .license-container {
    width: 100%;
    display: flex;
    flex-direction: column;
  }
</style>
