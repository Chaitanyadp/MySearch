<template>
  <div id="app">
    <ul id="nav">
      <li><img src="./assets/web-search-engine.png" width="50px" ></li>
      <li><a class="mytitle" href="localhost:8080">MySearch</a></li>
      <li class="git" style="float:right;"><a href="https://github.com/chaitanyadp">Github</a></li>
    </ul>
    <div v-if="loading" class="loader-div">
      <span class="loader">
        <span></span>
        <span></span>
      </span>
    </div>
    <div class="bckcolor">
      <br><br>
      <Searchbar @start-search="performSearch($event)"/>
      <Results :resultsList="searchedResults"/>
    </div>
  </div>  
</template>

<script>
import Searchbar from './components/Searchbar.vue'
import Results from './components/Results.vue'
const axios = require("axios");

export default {
  name: 'App',
  components: {
    Searchbar,
    Results
  },
  data() {
    return {
      loading: false,
      searchedResults: []
    }
  },
  methods: {
    performSearch(str) {
      console.log("Tested with string", str);
      this.loading = true;
      axios({
        "method":"GET",
        "url":"https://contextualwebsearch-websearch-v1.p.rapidapi.com/api/Search/WebSearchAPI",
        "headers":{
        "content-type":"application/octet-stream",
        "x-rapidapi-host":"contextualwebsearch-websearch-v1.p.rapidapi.com",
        "x-rapidapi-key":"bc046dd18fmshbfbf73133d35c0dp14fdbbjsnd445bf00d892",
        "useQueryString":true
        },"params":{
        "pageNumber":"1",
        "q":str,
        "autoCorrect":"true",
        "pageSize":"10"
        }
      })
      .then((response)=>{
        // console.log(response)
        this.loading = false;
        this.searchedResults = response.data.value;
      })
      .catch((error)=>{
        console.log(error)
      }).then(()=>{

      })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.bckcolor {
  background: linear-gradient(90deg, #e3ffe7 0%, #d9e7ff 100%);
  min-height: 94vh;
  width: 100%;
}

.git{
  position: relative;
  top: 12px;
  left: 5px;
}

.mytitle {
  position: relative;
  top: -10px;
  left: 50px;
}

img {
  position: relative;
  top: 5px;
  left: 60px;
}

#nav {
  position: fixed;
  width: 100%;
  text-align:center;
  background: linear-gradient(90deg, #d53369 0%, #daae51 100%);
  padding-bottom: 5px;
}

#nav li {
display:inline-block;
font-size: 30px;
font-weight: 700;
font-style: oblique;
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
line-height: 30px;
}

#nav a {
text-decoration:none; 
padding:0 30px; /* variable width */
color: rgb(11, 58, 119);
}
* {
  margin: 0;
  padding: 0;
  top: 0;
  box-sizing: border-box;
}

.loader-div {
	position: fixed;
	top: 0;
	left: 0;
	background-color: #333;
	height: 100vh;
	width: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
}

.loader {
	position: relative;
	width: 10vw;
	height: 5vw;
	padding: 1.5vw;
	display: flex;
	align-items: center;
	justify-content: center;
}

.loader span {
	position: absolute;
	height: 0.8vw;
	width: 0.8vw;
	border-radius: 50%;
	background-color: #ff0;
}

.loader span:nth-child(1) {
	animation: loading-dotsA 0.5s infinite linear;
}

.loader span:nth-child(2) {
	animation: loading-dotsB 0.5s infinite linear;
}

@keyframes loading-dotsA {
	0% {
		transform: none;
	}
	25% {
		transform: translateX(2vw);
	}
	50% {
		transform: none;
	}
	75% {
		transform: translateY(2vw);
	}
	100% {
		transform: none;
	}
}

@keyframes loading-dotsB {
	0% {
		transform: none;
	}
	25% {
		transform: translateX(-2vw);
	}
	50% {
		transform: none;
	}
	75% {
		transform: translateY(-2vw);
	}
	100% {
		transform: none;
	}
}

</style>
