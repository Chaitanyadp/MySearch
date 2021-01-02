<template>
  <div class="search-box">
    <input 
      type="text" 
      class="search-bar"
      placeholder="Search the web without being tracked"
      v-model="selfdata" 
      @keyup.enter="onChange()"
    />
    <button class="button effect" @click="onChange()">Search</button>
  </div>
</template>

<script>
export default {
  name: 'Searchbar',
  props: {
  },
  data() {
    return {
      selfdata: ""
    }
  },
  methods: {
    onChange() {
      this.$emit('start-search',this.selfdata);
      console.log(this.selfdata);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.search-box{
  display: inline-flex;
  width: 70%;
  margin-bottom: 30px;
  margin: 0 auto;
}
.search-box .search-bar{
  width: 100%;
  padding: 15px;
  color: #313131;
  font-size: 20px;
  
  appearance: none;
  outline: none;
  border: none;
  background: none;

  box-shadow: 0px 0px 8px rgba(0,0,0,.25);
  background-color: rgba(255,255,255,.5);
  border-radius: 15px 0px 15px 0px;
  transition: .5s;
}

.search-box .search-bar:focus{
  box-shadow: 0px 0px 16px rgba(0,0,0,.25);
  background-color: rgba(255,255,255,.5);
  border-radius: 0px 15px 0px 15px;
}

.button {
  display: inline-flex;
  box-sizing: border-box;
  appearance: none;
  background-color: transparent;
  border: 2px solid #e74c3c;
  border-radius: 0.6em;
  color: #e74c3c;
  align-self: center;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1;
  margin-left: 40px;
  padding: 1.2em 2.8em;
  text-decoration: none;
  text-transform: uppercase;
  font-family: 'Montserrat', sans-serif;
  font-weight: 700;
  cursor: pointer;

  &:hover,
  &:focus {
    color: rgb(255, 255, 255);
    outline: 0;
  }
}

.effect {
  border-color: #ccc;
  color: rgb(0, 0, 0);
  box-shadow: 0 0 40px 40px #3498db inset, 0 0 0 0 #3498db;
  transition: all 150ms ease-in-out;
  
  &:hover {
    background: linear-gradient(90deg, #d83e71 0%, #daae51 100%);
    box-shadow: 0 0 10px 0 #3498db inset, 0 0 10px 4px #3498db;
  }
}
</style>
