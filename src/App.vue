<template>
  <head>
    <div>
      <img src="imagenes/logo.jpg" align="right" width="150" height="100" />
    </div>
  </head>

  <body>
    <header id="main-header">
      <a id="logo-header" href="imagenes\salud1.jpg">
        <span class="site-name">Programa Pacientes Psp</span>
      </a>

      <nav>
        <ul>
          <li><a href="listar#/listar">Ver paciente</a></li>
          <li><a href="listar#/crear">Crear Paciente</a></li>
          <li><a href="listar#/Registrar">Registro Eventos</a></li>
		  <li><a href="listar#/listarEventos">Ver Eventos</a></li>
        </ul>
      </nav>
    </header>

    <br />

    <router-view> </router-view>
    <div>
      <legend><h3>Bienvenidos al Programa Pacientes Psp</h3></legend>
    </div>
  </body>
  <footer>
    <p>Creado por Grupo 4 Mision Tic 2021</p>
  </footer>
</template>
<script>
export default {
  name: "App",

  methods: {
    irAListapaciente: function () {
      this.$router.push({ name: "listarE" });
    },
    irACrearpaciente: function () {
      this.$router.push({ name: "crearE" });
    },
    irARegistroeventos: function () {
      this.$router.push({ name: "registrarE" });
    },
  },
};
</script>
<style>
.body {
  margin: 0 0 0 0;
  padding: 0;
  font-family: Helvetica, Arial, sans-serif;
  color: #666;
  background: #f2f2f2;
  font-size: 1em;
  line-height: 1.5em;
}
.header {
  position: fixed;
  margin: 0;
  padding: 5px 10px;
  width: 100%;
  height: 10vh;
  min-height: 100px;
  background-color: #283747;
  color: #e5e7e9;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.header h1 {
  width: 20%;
  text-align: center;
}

input,
textarea {
  margin: bottom 20px;
  width: 50%;
  border: 1px solid rgb(32, 28, 28);
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
.form {
  background: #ccc;
  width: 5%;
  border: 1px solid #ccc;
  margin: 20px;
  padding: 20%;
  display: flex;
  justify-content: center;
}
input:focus,
textarea {
  border: 1px solid#746c3e;
}
label {
  display: block;
  margin: 0.5em 0 0 0;
  width: 60px;
}

div {
  margin: 0.4em 0;
}
div label {
  width: 25%;
  float: left;
}

select {
  background: #e5e7e9;
  width: 50%;
  border: #ccc;
  font-size: 14px;
  height: 30px;
  padding: 5px;
  width: 250px;
  border-top-left-radius: 15px;
}
option{
	border-radius: 5px;
}
select:focus {
  outline: none;
}

* {
  margin: 0px;
  padding: 0px;
}

#header {
  margin: auto;
  width: 500px;
  font-family: Arial, Helvetica, sans-serif;
}

h1 {
  font-size: 2.3em;
  line-height: 1.3em;
  margin: 15px 0;
  text-align: center;
  font-weight: 300;
}

p {
  margin: 0 0 1.5em 0;
}

img {
  max-width: 100%;
  height: auto;
}
#main-header {
  background: #333;
  color: white;
  height: 80px;
}
#main-header a {
  color: white;
}

#logo-header {
  float: left;
  padding: 15px 0 0 20px;
  text-decoration: none;
}
#logo-header:hover {
  color: #0b76a6;
}

#logo-header .site-name {
  display: block;
  font-weight: 700;
  font-size: 1.2em;
}

#logo-header .site-desc {
  display: block;
  font-weight: 300;
  font-size: 0.8em;
  color: #999;
}

nav {
  float: right;
}
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
  padding-right: 20px;
}

nav ul li {
  display: inline-block;
  line-height: 80px;
}

nav ul li a {
  display: block;
  padding: 0 10px;
  text-decoration: none;
}

nav ul li a:hover {
  background: #0b76a6;
}

#main-header {
  background: #333;
  color: white;
  height: 80px;

  width: 100%;
  left: 0;
  top: 0;
}
</style>