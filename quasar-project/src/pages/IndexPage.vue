<template>
  <div id="root">
    <img id="backgroundImage" src="../../src/assets/utro-ozero-tuman-priroda-osen.jpg" alt="backgroundImage">
    <div></div>

    <q-card class="my-card text-white" style="background: radial-gradient(circle, #35a2ff 0%, #014a88 100%)">
      <q-card-section>
        <div class="text-h6">Select city</div>

        <q-input v-model="search" filled type="search" hint="Search..." v-model:model-value="data.city"
          @keyup.enter="getApi()">
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>


        <div class="mainn" v-bind:class="{}">
          <div class="search-box">

            <div >
              <div class="header">
                <p>{{data.weather.name}}</p>
                <h5>{{ new Date().toLocaleString() }}</h5>
              </div>
              <div class="temp">
                <p>С&deg;</p>
                <p>min</p>
                <p>max</p>
                <p>
                  <img class="icons" src="../assets/icons/free-icon-humidity-2828582.png" alt="">
                </p>
                <p>
                  <img class="icons" src="../assets/icons/free-icon-blood-pressure-3738867.png" alt="">
                </p>
                <p>
                  <img class="icons" src="../assets/icons/free-icon-wind-615486.png" alt="">
                </p>
              </div>
              <div class="state">
                <h3></h3>
              </div>
            </div>
          </div>
        </div>


      </q-card-section>

    </q-card>

  </div>
</template>

<script>
import axios from "axios"
import { ref } from "vue";
const apiKey = "b837277aa3e480cbbfe0d5bf056b97c1";
const apiUrl = 'https://api.openweathermap.org/data/2.5/weather';
const weatherdata = ref({});


export default {
  name: 'weather-app',
  data() {
    return {
      data: {
        city: '',
        weather: null,
        current_day: '',
        state_weather: false,
        humidity: false,
        pressure: false,
        wind: false,
      }
    }
  },
  mounted: async function () {
    this.getApi()
  },
  methods: {

    async getApi() {
      try {
        fetch(`${apiUrl}?q=${this.data.city}&appid=${apiKey}`)
          .then(function (resp) { return resp.json() })
          .then(function (data) {
            console.log(data)
            console.log(data.name)
            console.log(data)
            console.log(data.main.temp)

          })
      } catch (error) {
        console.log(error);
      }
    }
  }


  // methods: {
  //   async getApi() {



  //     if (this.data.city === '') {
  //       this.data.city = 'Bishkek'
  //     }
  //     const getWeather = await axios.get(`${apiUrl}?q=${this.data.city}&appid=${apiKey}`)
  //     console.log(getWeather);
  //     this.data.weather = getWeather.data
  //     this.data.city = ''
  //     if (this.data.weather.main.temp > 16) {
  //       this.state_weather = true
  //     } else {
  //       this.state_weather = false
  //     }
  //     console.log(data)
  //   },
  // },
};

</script>



<style setup>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

#backgroundImage {
  width: 100%;
  position: fixed;
}

.q-card {
  width: 25%;
  height: 70vh;
  margin-left: 35%;
  position: absolute;
  margin-top: 5%;
}

.mainn {
  min-height: 5vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(18, 75, 156, 0.35), rgba(2, 15, 22, 0.75));
}

.mainn.warm {
  min-height: 5vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(248, 8, 8, 0.35), rgba(246, 6, 6, 0.75));
}

.temp {
  display: inline-block;
  display: flex;
  flex-direction: column;
  padding: 5%;
  color: #FFF;
  font-size: 15px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0px;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.header {
  font-size: 20px;
  color: azure;
  box-shadow: rgba(3, 3, 3, 0.3);
}

.icons {
  width: 10%;
}
</style>