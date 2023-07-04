<template>
  <nav class="container-fluid">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-1"></div>
        <div class="col-md-9">
          <router-link to="/" id="izq"><img src="./assets/game.png">Game Opinion</router-link>
        </div>
        <div class="col-md-2">
          <router-link to="/" id="der1">Home</router-link> |
    <router-link to="/about" id="der2">About</router-link>
        </div>
      </div>
    </div>    
  </nav>
  <router-view/>
  <footer id="mi_footer" class="mifooter">
      <b> <p class="mifooter__eltextoreservado">TODOS LOS DERECHOS RESERVADOS ® J.U.</p> <!--&#174 codigo acci--> </b>    
  </footer>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
  background-color: black;
  color: white;
  text-align: start;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
#izq{
  text-align: start;
}
#der1{
 text-align: end;
}
.mifooter {   
    border: 2px solid blueviolet;
    background-image: linear-gradient(90deg, #d108c0 0%, #acf570 100%);
  }
  
  .mifooter__eltextoreservado {
    font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
    color: rgb(8, 8, 8);
  }
</style>
