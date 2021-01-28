<template>
  <div id="app">
    <Navbar />

    <div class="container">
      <div class="container2">
        <h1>Github Search</h1>
        <input @keyup="getUser" id="search" type="text" class="from-control" placeholder="digite para encontrar usuarios" required />
        <a :href="user.html_url" target="_blank" ><input class="btn" type="submit"  value=" " /></a>


      </div>
      <div class="row" v-if="user.length !== 0" >
        <div class="row1">
          <Profile :user="user" />
        </div>

        <div class="row2">
          <Repos v-for="repos in repos" :key="repos" :repos="repos" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import Navbar from './components/Navbar';
import Profile from './components/Profile';
import Repos from './components/Repos';
import axios from 'axios';

export default {
  name: 'App',
  data(){
    return{
      api:{
        url:'https://api.github.com/users',
        client_id:'37f133c5fc0bc67166e3',
        client_secret:'f2f03f09a360a5223243bac3508124eea6ae3a32',
        count: 7,
        sort: "created: asc"
      },
      user:[],
      repos:[]
    };
  },
  components:{
    Navbar,
    Profile,
    Repos
  },
  methods:{
    getUser(e){
      const user = e.target.value;
      const { url, client_id, client_secret, count, sort} = this.api

      axios.get(`${url}/${user}?client_id=${client_id}&client_secret=${client_secret}`).then(({data}) => this.user = data);

      axios.get(`${url}/${user}/repos?per_page=${count}&sort=${sort}&client_id=${client_id}&client_secret=${client_secret}`).then(({ data }) => this.repos = data);
    }
  }

};
</script>

<style>
.container2{
  margin: 100px auto;
  padding: 50px;
  width: 312px;
  text-align: center;
  background-color: #b4b4b4;
  border-radius: 10px;
} 

input{
  padding: 5px;

}
.btn{
  background-image:url("../icon/lupa.png");
  background-repeat: no-repeat;
  background-size:contain;
  background-color: white;
  background-position: center;
  width: 55px;
  cursor: pointer;
  border: none;
  padding: 6px;;
}

.row1{
  margin-top: -40px;
  text-align: justify;

}

.row2{
  display: flex;
  margin: 10px;

}


</style>
