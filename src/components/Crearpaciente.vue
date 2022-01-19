<template>
  <form>
    <fieldset>
      <legend><h2>Crear paciente</h2></legend>
      <br /><br />
      <div class="container_form">
        <div class="form-group">
          <label>Nombres:</label>
          <input v-model="paciente.Nombres" />
        </div>
        <br />
        <div div class="form-group">
          <label>Apellidos:</label>
          <input v-model="paciente.Apellidos" />
        </div>
        <br />
        <div class="form-group">
          <label>No_Identificación: </label>
          <input v-model="paciente.No_documento" />
        </div>
        <br />
        <div class="form-group">
          <label>Dirección:</label>
          <input v-model="paciente.Direccion" />
        </div>
        <br />
        <div class="form-group">
          <label>Telefono:</label>
          <input v-model="paciente.Telefono" />
        </div>
        <br />
        <div class="form-group">
          <label>Telefono_2:</label>
          <input v-model="paciente.Telefono1" />
        </div>
        <br />

        <div class="form-group">
          <label>Ciudad:</label>
          <input v-model="paciente.Ciudad" />
        </div>
        <br />

        <div class="form-group">
          <label>Tutor_Responsable: </label>
          <input v-model="paciente.Nombre_responsable" />
        </div>
        <br />
        <div class="form-group">
          <label>Tel_Tutor_Responsable:</label>
          <input v-model="paciente.Telefono_responsable" />
        </div>
        <br />
        <div class="form-group">
          <label>Tel2_Tutor_Responsable: </label>
          <input v-model="paciente.Telefono1_responsable" /><br />
        </div>
        <br />
      </div>
      <button class="btn" v-on:click="crearpaciente">Crear</button>
      <br />
      <br />
      <div></div>
    </fieldset>
  </form>
</template>

<script>
import axios from "axios";

export default {
  name: "crearpaciente",

  data: function () {
    return {
      paciente: {
        Nombres: "",
        Apellidos: "",
        No_documento: "",
        Direccion: "",
        Telefono: "",
        Telefono1: "",
        Ciudad: "",
        Nombre_responsable: "",
        Telefono_responsable: "",
        Telefono1_responsable: "",
      },
    };
  },

  methods: {
    crearpaciente: function () {
      axios
        .post("https://psp-back-01.herokuapp.com/paciente/", this.paciente)
        .then((respuesta) => {
          this.paciente.Nombres = "";
          this.paciente.Apellidos = "";
          this.paciente.No_documento = "";
          this.paciente.Direccion = "";
          this.paciente.Telefono = "";
          this.paciente.Telefono1 = "";
          this.paciente.Ciudad = "";
          this.paciente.Nombre_responsable = "";
          this.paciente.Telefono_responsable = "";
          this.paciente.Telefono1_responsable = "";

          alert(respuesta.data.mensaje);
        })
        .catch((error) => {
          alert("Error creando el paciente");
          console.log(error);
        });
    },
  },
};
</script>

<style>
label {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  padding: 1px;
}

form {
  padding: 20px 15%;
}

input {
  padding: 10px;
  background-color: rgba(0, 255, 255, 0.075);
  width: 45%;
  margin-right: 100px;
  border-radius: 15px;
}

.form-group label {
  width: 35%;
  text-align: right;
}

@media (max-width: 768px) {
  form {
    padding: 20px 5%;
  }
  input {
    padding: 7px;
    background-color: rgba(0, 255, 255, 0.123);
    width: 45%;
    margin-right: 5px;
  }
  .form-group label {
    width: 35%;
    text-align: right;
    font-size: 15px;
  }
}
</style>