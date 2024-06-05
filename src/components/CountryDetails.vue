<script setup>
import { ref, onMounted } from 'vue';
import { RouterLink, useRoute } from 'vue-router';
import NavBar from './NavBar.vue';

const countries = ref([]);
const route = useRoute();

onMounted(async () => {
  try {
    const response = await fetch(`countries.json`);
    const data = await response.json(); 
    countries.value = data;
    const id = route.params.alpha3Code;
    console.log(countries.value);
  } catch (error) {
    console.error('Error fetching countries:', error);
  }
}); 
</script>

<template>
<div class="col-7">
    <img src="https://restcountries.eu/data/fra.svg" alt="country flag" style="width: 300px"/>
    <h1>France</h1>
    <table class="table">
      <thead></thead>
      <tbody>
        <tr>
          <td style="width: 30%">Capital</td>
          <td>Paris</td>
        </tr>
        <tr>
          <td>Area</td>
          <td>
            551695 km <sup>2</sup>
          </td>
        </tr>
        <tr>
          <td>Borders</td>
          <td>
            <ul>
              <li><a href="/AND">Andorra</a></li>
              <li><a href="/BEL">Belgium</a></li>
              <li><a href="/DEU">Germany</a></li>
              <li><a href="/ITA">Italy</a></li>
              <li><a href="/MCO">Monaco</a></li>
              <li><a href="/ESP">Spain</a></li>
              <li><a href="/CHE">Switzerland</a></li>
            </ul>  
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style></style>