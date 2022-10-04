<template>
  <div>
    <car-form />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import CarForm from './components/forms/carForm.vue';

@Options({
  components: {
    CarForm,
  },
})
export default class App extends Vue {}
</script>

<style>
/* @import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,300;1,400;1,500;1,600;1,700;1,800&display=swap');
* {
  font-family: 'Open Sans', sans-serif;
} */
*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    background-color: rgb(254, 254, 254);
  }

/* Paragraph and subtitles fonts */
@font-face {
    font-family: "Roboto";
    src: url(assets/fonts/Roboto/roboto-v29-latin-300.woff2);
    font-style: normal;
    font-weight: 300;
}

@font-face {
    font-family: "Roboto";
    src: url(assets/fonts/Roboto/roboto-v29-latin-300italic.woff2);
    font-style: italic;
    font-weight: 300;
}

@font-face {
    font-family: "Roboto";
    src: url(assets/fonts/Roboto/roboto-v29-latin-700.woff2);
    font-style: normal;
    font-weight: 700;
}

/* Title fonts */
@font-face {
    font-family: "Roboto Slab";
    src: url(assets/fonts/Roboto_Slab/roboto-slab-v16-latin-300.woff2);
    font-style: normal;
    font-weight: 300;
}

@font-face {
    font-family: "Roboto Slab";
    src: url(assets/fonts/Roboto_Slab/roboto-slab-v16-latin-regular.woff2);
    font-style: normal;
    font-weight: 400;
}

@font-face {
    font-family: "Roboto Slab";
    src: url(assets/fonts/Roboto_Slab/roboto-slab-v16-latin-700.woff2);
    font-style: normal;
    font-weight: 700;
}

/* Mobile Styles */

h1, h2 {
    font-family: "Roboto Slab", serif;
    font-weight: 300;

    line-height: 1.5em;
    margin-bottom: 1.5em;
}

h3, h4, h5, h6, button {
    font-family: "Roboto", sans-serif;
    font-weight: 400;
    font-style: normal;

    line-height: 1.5em;
    margin-bottom: 1.5em;
}

p, li, label, input, textarea, option, select {
    font-family: "Roboto", sans-serif;
    font-style: normal;
    font-weight: 300;

    text-align: left;

    line-height: 1.5em;
    margin-bottom: 1.5em;
}

strong {
    font-family: "Roboto", sans-serif;
    font-style: normal;
    font-weight: 700;

    text-align: left;

    line-height: 1.5em;
    margin-bottom: 1.5em;
}

button {
    padding-top: 0.5em;
    padding-bottom: 0.5em;
    padding-right: 1em;
    padding-left: 1em;
    margin-top: 1em;

    border: 2px solid #0cbe3b;
    border-radius: 10px;

    background-color: white;
}

button:hover {
    transition: all 0.3s ease;
    background-color: #0ed642;
    color: white;
}

input, textarea, option, select {
    padding-top: 0.5em;
    padding-bottom: 0.5em;

    border: 1px solid #0cbe3b;
    border-radius: 3px;

    background-color: white;
}

input:focus, select:focus {
    border: 1px solid #0ed642;
}

/* Font sizes */

h1 {
    font-size: 30px;
}

h2 {
    font-size: 25px;
}

h3, h4, h5, h6, button {
    font-size: 20px;
}

p, li, label, input, textarea, option, select {
    font-size: 14px;
}

@media only screen and (min-width:401px){

/* max width size for the text */

p, h1, h2, h3, h4, h5, h6, li, ol, ul, input, label, textarea, select, option {
    max-width: 580px;
}

/* Font sizes */
h1 {
    font-size: 40px;
}

h2 {
    font-size: 35px;
}

h3, h4, h5, h6, button {
    font-size: 25px;
}

p, li, label, input, textarea, select, option {
    font-size: 16px;
}
}

/* Desktop Styles */
@media only screen and (min-width: 961px) {
/* max width size for the text */

p, h1, h2, h3, h4, h5, h6, li, ol, ul, label, input, textarea, select, option {
    max-width: 700px;
}

/* Font sizes */
h1 {
    font-size: 50px;
}

h2 {
    font-size: 45px;
}

h3, h4, h5, h6, button {
    font-size: 30px;
}

p, li, label, input, textarea, option, select {
    font-size: 20px;
}
}
</style>
