<template>
  <div class="carstable">
    <div>
      <select v-model="date_selected">
        <option v-for="date in dates" :key="date" :value="date">{{ date }}</option>
      </select>
    </div>
    <div :hidden="date_selected.length === 0">
      <h1>{{ date_selected }}</h1>
    <table :hidden="cars.length == 0">
      <thead>
        <tr>
          <th>Brand</th>
          <th>Model</th>
          <th>Year</th>
          <th>Mileage</th>
          <th>Power</th>
          <th>Capacity</th>
          <th>Fuel</th>
          <th>Color</th>
          <th>Used or new</th>
          <th>Doors</th>
          <th>Gearbox</th>
          <th>Location</th>
          <th>City</th>
          <th>Region</th>
          <th>Price</th>
          <th>lat</th>
          <th>lon</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="car in cars" :key="car.make">
          <td>{{ car.brand }}</td>
          <td>{{ car.model }}</td>
          <td>{{ car.year }}</td>
          <td>{{ car.mileage }}</td>
          <td>{{ car.power }}</td>
          <td>{{ car.capacity }}</td>
          <td>{{ car.fuel }}</td>
          <td>{{ car.color }}</td>
          <td>{{ car.usedornew }}</td>
          <td>{{ car.doors }}</td>
          <td>{{ car.gearbox }}</td>
          <td>{{ car.location }}</td>
          <td>{{ car.city }}</td>
          <td>{{ car.region }}</td>
          <td>{{ car.price }}</td>
          <td>{{ car.lat }}</td>
          <td>{{ car.lon }}</td>

        </tr>
      </tbody>
    </table>
    </div>
    
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'CarsTable',

  data () {
    return {
      cars: [],
      date_selected: '',
      dates: [],
    }
  },
  methods: {
    fetchCars () {
      axios.get(`http://localhost:8000/cars/2019-01-12`)
        .then(response => {
          console.log(response.data)
          this.cars = response.data.cars
        })
    },

    fetchDates () {
      axios.get(`http://localhost:8000/dates`)
        .then(response => {
          console.log(response.data)
          this.dates = response.data.dates
        })
    }
  },

  mounted () {
    // this.fetchCars()
    this.fetchDates()
  },

  watch: {
    date_selected: function () {
      this.cars = []
      axios.get(`http://localhost:8000/cars/${this.date_selected}`)
        .then(response => {
          console.log(response.data)
          this.cars = response.data.cars
        })
    }
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
