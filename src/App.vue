<template>
  <div id="root" class="container">
    <HelloWorld msg="Bienvenue sur notre site de commande en ligne" />
    <ContentPage />
  </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ContentPage from './components/ContentPage.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    ContentPage
  }
}
</script>

<style>
@import './styles/reset.css';
* {
  box-sizing: border-box;
}
html {
  margin:0;
  padding:0;
  height: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #B7E1D5;
  background-color: #699488;
  min-height: 100vh;
  width: 100%;
  overflow: hidden;
}
body {
  margin: 0;
}
h1 {
  font-size: 3rem;
  margin: 1rem;
}
h2 {
  font-size: 2rem;
}
h3 {
  font-size: 1.5rem;
}
h4 {
  font-weight: bold;
}

.container {
  padding: 0 7%;
  width: 100%;
  margin-top: 1rem;
  display:flex;
  align-items: center;
  flex-direction: column;
}
.flash {
  position: fixed;
  color: black;
  display: flex;
  align-items: center;
  padding: 2rem;
  top:15px;
  left: 15px;
  background-color: #F9AFA0;
  transition: all 0.3s ease-out;
  opacity: 0.8;
  border-radius: 15px;
}
.flashIsHidden {
  left:-600px;
  opacity: 0;
}
.connect {
  font-weight: bold;
  }

.login {
  line-height: 2.3rem;
  background-color: #B7E1D5;
  color: #2c3e50;
  border: none;
  border-radius: 5px;
  padding-left: 1rem;
  margin: 0 1rem;
}
.row {
  padding: 0 5%;
  display: flex;
}
.label {
  font-size: 1.3rem;
  align-self: center;
}
.cards {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.cards-deck {
  display: flex;
  width: 100%;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
.btn {
  padding: 0.7rem;
  margin: 0.5rem;
  background-color: #2c3e50;
  border: none;
  border-radius: 5px;
  color:#B7E1D5;
}
.card {
  width: 25%;
  min-width: 25%;
  border: 2px solid  #94675A;
  border-radius: 5px;
  margin: 0.3rem;
  padding: 0.5rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.card-content {
  display: flex;
  width: 100%;
  justify-content: space-between;
  padding: 0.3rem;
}
.card-title {
  font-size: 1.3rem;
  font-weight: bold;
  align-self: center;
}
.card-price {
  border: 1px solid #B7E1D5;
  border-radius: 50%;
  height: 60px;
  line-height: 60px;
  text-align: center;
  width: 60px;
}
.flash-command {
  background-color: lightgreen;
  display:flex;
  flex-direction: column;
}

.flash-command li{
  margin-left: 2rem;
  list-style-type: "\1F44D";
  padding-left: 1rem;
}
@media (max-width: 960px) {
  h1 {
    font-size: 2rem;
  }
  .card {
    width:100%;
  }
  .connect {
    text-align: center;
    flex-direction: column;
  }
  .cards-title {
    font-size: 1.7rem;
  }
  .flash {
    right: 15px;
  }
}
</style>
