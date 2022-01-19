<template>
  <fieldset>
    <legend><h2>Consulta Paciente</h2></legend>
    <br />
    <br />

    <div class="container">
      <div v-for="paciente in Listapacientes" class="cuadro_contenedor">
        <div class="create-route">
          <b>Codigo:</b>
          <p>{{ paciente.id }}</p>
        </div>
        <div class="create-route">
          <b> Nombres:</b>
          <p>{{ paciente.Nombres }}</p>
        </div>
        <div class="create-route">
          <b>Apellidos:</b>
          <p>{{ paciente.Apellidos }}</p>
        </div>
        <div class="create-route"> 
          <b>No_documento:</b>
          <p>{{ paciente.No_documento }}</p>
        </div>
        <div class="create-route">
          <b>Direccion:</b>
          <p>{{ paciente.Direccion }}</p>
        </div>
        <div class="create-route">
          <b>Telefono:</b>
          <p>{{ paciente.Telefono }}</p>
        </div>
        <div class="create-route">
          <b>Telefono1:</b>
          <p>{{ paciente.Telefono1 }}</p>
        </div>
        <div class="create-route">
          <b>Nombre_responsable:</b>
          <p>{{ paciente.Ciudad }}</p>
        </div>
        <div class="create-route">
          <b>Nombre_responsable:</b>
          <p>{{ paciente.Nombre_responsable }}</p>
        </div>
        <div class="create-route">
          <b>Telefono_responsable:</b>
          <p>{{ paciente.Telefono_responsable }}</p>
        </div>
        <div class="create-route">
          <b>Telefono1_responsable:</b>
          <p>{{ paciente.Telefono1_responsable }}</p>
        </div>
        <div></div>
        <div></div>
        <button class="btn" v-on:click="BorrarPaciente(paciente.id)">eliminar</button>
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
      Listapacientes: [],
    };
  },

  methods: {
    BorrarPaciente: function (id) {
      axios
        .delete("https://psp-back-01.herokuapp.com/paciente/" + id)
        .then((respuesta) => {
          alert("El paciente se eliminó exitosamente ");
          this.actualizarLista();
        })
        .catch((error) => {
          alert("Error borrando el paciente");
          console.log(error);
        });
    },

    irAActualizarPaciente: function (paciente) {
      this.$router.push({
        name: "actualizarE",
        params: {
          id: paciente.id,
          nombre: paciente.nombre,
          cedula: paciente.cedula,
        },
      });
    },

    actualizarLista: function () {
      axios
        .get("https://psp-back-01.herokuapp.com/paciente/")
        .then((respuesta) => {
          this.Listapacientes = respuesta.data;
        })
        .catch((error) => {
          alert("Error obteniendo los paciente");
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
</style>