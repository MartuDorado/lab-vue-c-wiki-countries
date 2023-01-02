<template>
   <div v-if="country !=null" class="col-7">
            <img :src="
                    'https://flagpedia.net/data/flags/icon/72x54/' +
                    country.alpha2Code +
                    '.png'
                  "/>
            <h1>{{country.name}}</h1>
            <table class="table">
              <thead></thead>
              <tbody>
                <tr>
                  <td style="width: 30%">Capital</td>
                  <td>{{country.capital}}</td>
                </tr>
                <tr>
                  <td>Area</td>
                  <td>
                    {{country.area}} <sup>2</sup>
                  </td>
                </tr>
                <tr>
                  <td>Borders</td>
                  <td>
                    <ul>
                      <li v-for="border in country.borders">
                        <a href="#">{{ border }}</a>
                      </li>
                     
                    </ul>  
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
  
</template>
<script>
export default{
  props: {
    country: {
      type: Object,
      // required: true,
      default: {
        name: "Argenina",
        capital: "CABA",
        area: " ",
        borders: [],
        alpha3code: "ARG",
        alpha2code:" "
      }
    }
  }
}
</script>
