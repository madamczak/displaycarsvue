<template>
  <div class="carstable">
    <table>
      <thead>
        <tr>
          <th>Date</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="date in dates" :key="date">
          <td><a href="">{{ date }}</a></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'DatesSelect',

  data () {
    return {
      dates: [],
      date_selected: '2021-01-11'
    }
  },
  methods: {
    fetchDates () {
      axios.get(`http://localhost:8000/dates`)
        .then(response => {
          console.log(response.data)
          this.dates = response.data.dates
        })
    }
  },

  mounted () {
    this.fetchDates()
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.carstable {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

th, td, table {
  border: 1px solid black;
  border-collapse: collapse;
}

</style>
