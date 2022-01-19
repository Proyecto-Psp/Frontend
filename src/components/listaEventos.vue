<template>
  <fieldset>
    <legend><h2>Consulta Notas</h2></legend>
    <br />
    <br />
    <div class="container">
      <div v-for="nota in Listanotas" class="cuadro_contenedor">
        <div class="create-route">
          <b> Codigo:</b>
          <p>{{ nota.id_nota }}</p>
        </div>
        <div class="create-route">
          <b> Fecha:</b>
          <p>{{ nota.fecha }}</p>
        </div>
        <div class="create-route">
          <b>Usuario</b>
          <p>{{ nota.usuario }}</p>
        </div>
        <div class="create-route">
          <b>Profesional en gestión:</b>
          <p>{{ nota.profesional_en_gestion }}</p>
        </div>
        <div class="create-route">
          <b>Fecha de proxima gestión:</b>
          <p>{{ nota.fecha_proxima_gestion }}</p>
        </div>
        <div class="create-route">
          <b>Fecha de ultima gestión:</b>
          <p>{{ nota.fecha_ultima_gestion }}</p>
        </div>
        <div class="create-route">
          <b>Estado en EPS:</b>
          <p>{{ nota.estado_en_eps }}</p>
        </div>
        <div class="create-route">
          <b>Estado tratamiento:</b>
          <p>{{ nota.estado_tratamiento }}</p>
        </div>
        <div class="create-route">
          <b>Nota</b>
          <p>{{ nota.nota }}</p>
        </div>
        <div class="create-route">
          <b>Diagnostico:</b>
          <p>{{ nota.diagnostico }}</p>
        </div>
        <div class="create-route">
          <b>Tratamiento:</b>
          <p>{{ nota.tratamiento }}</p>
        </div>
        <div></div>
        <div></div>
        <button class="btn" v-on:click="BorrarNota(nota.id_nota)">
          Eliminar
        </button>
      </div>
    </div>
  </fieldset>
</template>

<script>
import axios from "axios";

export default {
  name: "Listapaciente",
  data: function () {
    return {
      Listanotas: [],
    };
  },

  methods: {
    BorrarNota: function (id) {
      axios
        .delete("https://psp-back-01.herokuapp.com/nota/" + id)
        .then((respuesta) => {
          alert("La nota se eliminó exitosamente ");
          this.actualizarLista();
        })
        .catch((error) => {
          alert("Error borrando la nota");
          console.log(error);
        });
    },

    actualizarLista: function () {
      axios
        .get("https://psp-back-01.herokuapp.com/nota/")
        .then((respuesta) => {
          this.Listanotas = respuesta.data;
        })
        .catch((error) => {
          alert("Error obteniendo las notas");
          console.log(error);
        });
    },
  },

  created: function () {
    this.actualizarLista();
  },
};
</script>

<style>
.cuadro_contenedor {
  padding: 10px;
  margin-bottom: 10px;
  background-color: rgb(245, 245, 245);
  border: solid 1px red;
  display: grid;
  grid-template-columns: 33% 33% 33%;
  border-radius: 10px;
  box-shadow: 3px 3px 3px 2px rgba(197, 23, 23, 0.2);
}

.container{
    padding-left: 100px;
    padding-right: 100px;
}

.create-route {
  border-radius: 6px;
  text-align: left;
  margin: 2px;
  padding: 0px;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

.btn {
  color: rgb(143, 13, 13);
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  padding: 10px;
  font-size: 20px;
  box-shadow: 2px 2px 2px 1px rgba(197, 23, 23, 0.2);
  border-radius: 50px;
  margin-left: 50px;
  margin-right: 50px;
}

.btn:hover{
    color: white;
    background-color: red;
}

body {
  text-align: center;
}
</style>