<template>
  <div class="title">
    <h1>{{ msg }}</h1>
    <hr>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
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
.title {
  text-align: center;
  width: 70%;
}
hr {
  background-color: #94675A;
	margin: 40px 0 80px;
	padding: 0;
	border: 0;
	font-family: arial;
  text-align: center;
  height: 3px;
  border-radius: 20px;
  box-shadow:10px 10px 15px #94675A;
}

</style>
