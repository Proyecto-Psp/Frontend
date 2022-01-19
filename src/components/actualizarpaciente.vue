<template>
  <h1>Actualizar</h1>
  <form v-on:submit.prevent="actualizarpaciente">
    <input type="text" v-model="nombre" placeholder="nombre" />
    <br />
    <input type="text" v-model="cedula" placeholder="cedula" />
    <br />
    <button type="submit">Actualizar</button>
  </form>
</template>

<script>
import axios from "axios";
export default {
  name: "Actualizarpaciente",
  props: ["nombre", "cedula", "id"],
  methods: {
    actualizarpaciente: function() {
      axios
        .put("https://psp-back-01.herokuapp.com/paciente/" + this.id, {
          nombre: this.nombre,
          cedula: this.cedula,
        })
        .then((respuesta) => {
          alert("paciente actualizado exitosamente!");
        })
        .catch(() => {
          alert("Error al actualizar el paciente");
        });
    },
  },
  created: function() {},
};
</script>

<style></style>
