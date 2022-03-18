<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 20 ? 'warm' : '' ">
    <div class="container">
      <div class="search-box">
        <input type="text"
        class="search-bar" 
        placeholder="Search..."
        v-model="search"
        @keypress="searchWheater"
        />
       </div>
      
      <div class="wheater-wrapper" v-if="typeof weather.main !='undefined'">
        <div class="info-box">
          <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
          <div class="date">{{ dateGetter() }}</div>
        </div>

        <div class="wheater-box">
          <div class="temp"> {{ Math.round(weather.main.temp) }} °C</div>
          <div class="wheater"> {{weather.weather[0].main }} </div>
        </div>
      </div>
     </div>
  </div>
</template>

<script>


export default {
  

  name: 'App',
  components: {},
  data(){
    return{
      apiKey: process.env.API_KEY,
      API_KEY: 'https://api.openweathermap.org/data/2.5/',
      search: '',
      weather: {},
    }
  },

  methods: {
    //
    searchWheater(e) {
      if(e.key == 'Enter'){
        fetch(`${this.apiURI}weather?q=${this.search}&units=metric&APPID=${this.apiKey}`)
        .then(res => {
          return res.json();
        }).then(this.setResults);
      }
    },

    setResults(results) {
      this.weather = results;
    },

    dateGetter(){
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    }
  
  },

  mounted(){
    
  }
  }
  


</script>

<style >
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
}

#app .warm {
  background-image: url('./assets/warm-bg.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

#app{
  background-image: url('./assets/cold-bg.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}



.container{
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
}

.search-box{
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar{
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;

  appearance: none;
  border:thin;
  border-radius: 0px 16px 0px 16px;
  outline: none;
  background: none;

  background-color: rgba(255, 255, 255, 0.15);
  transition: 0.4s;
}

.search-box .search-bar:focus{
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}

.info-box .location{
  color: black;
  font-size: 35px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.info-box .date{
  margin-top: 1vh;
  color: black;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}

.wheater-wrapper{
  text-align: center;
}

.wheater-wrapper .temp{
  display: inline-block;
  padding: 10px 25px;
  color: #FFF;
  font-size: 85px;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0px;

  box-shadow: 3px 6px rgba(255, 255, 255, 0.25);
}

.wheater-wrapper .wheater{
  color: black;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}



</style>
