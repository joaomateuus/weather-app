<template>
  <div id="app">
    <div class="container">
      <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search..."/>
       </div>
      
      <div class="wheater-wrapper">
        <div class="info-box">
          <div class="location">Manaus,BR</div>
          <div class="date">Thusrday 17 March 2022</div>
        </div>

        <div class="wheater-box">
          <div class="temp">25°c</div>
          <div class="wheater">Sunny</div>
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
      apiKey: '954d710dc63014a43aaf61167742641a',
    }
  },

  methods: {

  },

}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
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
  color: #FFF;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.info-box .date{
  color: #FFF;
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
  color: #FFF;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}



</style>
