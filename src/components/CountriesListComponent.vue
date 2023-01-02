<template>
  <div class="container">
    <!-- Bootstrap row wrapper div -->
    <div class="row">
      <!-- Countries List (Bootstrap column) -->
      <div class="col-5" style="max-height: 90vh; overflow: scroll">
        <div class="list-group">
          <ul>
            <li v-for="(country, index) in countries" :key="country.alpha3Code">
              <router-link :to="`/list/${country.alpha3Code}`">
                {{ country.name }}
                <img
                  :src="
                    'https://flagpedia.net/data/flags/icon/72x54/' +
                    country.alpha2Code +
                    '.png'
                  "
                />
              </router-link>
            </li>
          </ul>
        </div>
      </div>
      <CountryDetailsComponent
        :country="selectedCountry"
      ></CountryDetailsComponent>
    </div>
  </div>
</template>
<script>
import CountryDetailsComponent from "./CountryDetailsComponent.vue";
export default {
  components: {
    CountryDetailsComponent,
  },
  data() {
    return {
      countries: [],
      selectedCountry: null,
    };
  },
  async created() {
    const response = await fetch(
      `https://ih-countries-api.herokuapp.com/countries`
    );
    const data = await response.json();
    const countryList = data;
    for (let i = 0; i < countryList.length; i++) {
      const country = {
        name: countryList[i].name.common,
        capital: countryList[i].capital[0],
        area: countryList[i].area,
        borders: countryList[i].borders,
        alpha3Code: countryList[i].alpha3Code,
        alpha2Code: countryList[i].alpha2Code.toLowerCase(),
      };
      this.countries.push(country);
    }
    console.log(this.countries);
  },

  watch: {
    "$route.params.alpha3Code"() {
      this.selectedCountry = this.countries.find(
        (country) =>
          country.alpha3Code == this.$route.params.alpha3Code.toUpperCase()
      );
    },
  },
};
</script>
