<template>
<div id="app">
  <div class="container">
      <router-view/>
  </div>
</div>
</template>

<style>
html{
  font-family: arial,sans-serif;
  color: gray;
}

body {
  padding: 0px;
  margin-bottom: 200px;
  background-image: url("assets/spiration dark.png");
}

 button {
  position: absolute;
  background-color: lightblue;
  margin: 400px;
 }

 h1 {
  color: orange;
 }

 p {
  color: grey;
 }

#pic {
  margin-top: 50px;
}
</style>
