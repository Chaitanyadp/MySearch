<template>
  <div class="oneresult">
    <a class="container" :href="url">
        <span v-html="title" class="title"></span><br>
        <span v-html="url" class="url"></span><br>
        <span v-html="desc" class="desc"></span><br><br>
    </a>
  </div>
</template>

<script>
export default {
  name: 'OneResult',
  props: {
    title: String,
    desc: String,
    url: String
  },
  data() {
    return {

    }
  },
  methods: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.oneresult {
    display:flex;
    text-align: left;
}
.title {
    font-size: 20px;
    color: #456fc9;
}
.url {
    font-size: 16px;
    color: #30ad7d;
}
.desc {
    font-size: 15px;
    color: #4e525c;
}
.container {
    padding:0 1rem;
    background: rgba(153, 217, 242, .0);
    text-decoration: none;
    border-bottom: 3px solid transparent;
    border-left: 3px solid transparent;
    border-top: 3px solid transparent;
    border-right: 3px solid transparent;
    /* transition: background .1s, border-bottom .2s, border-left .3s, border-top .4s, border-right .5s; */
}
.container:hover {
    background: rgba(153, 217, 242, 0.561);
    /* transition: background .9s, border-bottom .1s .2s, border-left .7s .8s, border-top .5s .6s, border-right .3s .4s; */
    border-bottom: 3px solid rgb(177, 186, 206);
    border-left: 3px solid rgb(177, 186, 206);
    border-top: 3px solid rgb(177, 186, 206);
    border-right: 3px solid rgb(177, 186, 206);
}
</style>
