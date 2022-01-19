<template>
  <form>
    <fieldset>
      <legend><h2>Registrar Eventos</h2></legend>

      <br />

      <div class="form-group">
        <label>Usuario:</label>
        <select v-model="nota.usuario" name="Usuario" id="">
          <option v-for="paciente in Listapacientes" v-bind:value="paciente.Nombres +' '+ paciente.Apellidos">
            {{ paciente.Nombres }} {{ paciente.Apellidos }}
          </option>
        </select>
      </div>
      <br />
      <div class="form-group">
        <label>Profesional_en_gestion:</label>
        <input v-model="nota.profesional_en_gestion" type="text" name="" id="" />
      </div>
      <br />
      <div class="form-group">
        <label>Fecha de próxima gestión</label>
        <input v-model="nota.fecha_proxima_gestion" type="datetime-local" id="start" />
      </div>
      <br />
      <div class="form-group">
        <label>Fecha de última gestión</label>
        <input v-model="nota.fecha_ultima_gestion" type="datetime-local" id="start" />
      </div>
      <br />
      <div class="form-group">
        <label>Estado en eps:</label>
        <select v-model="nota.estado_en_eps" name="EEps" id="">
          <option value="">Selecione</option>
          <option value="Activo">Activo</option>
          <option value="Supendido">Supendido</option>
          <option value="Desafiliado">Desafiliado</option>
        </select>
      </div>
      <br />
      <div class="form-group">
        <label>Estado de tratamiento:</label>
        <select v-model="nota.estado_tratamiento" name="Etratamiento" id="">
          <option value="">Seleccione</option>
          <option value="Activo">Activo</option>
          <option value="Supendido">Supendido</option>
          <option value="Desafiliado">Desafiliado</option>
        </select>
      </div>
      <br />

      <div class="form-group">
        <label>Nota: </label> <br />

        <textarea v-model="nota.nota" id="Nota" name="user_message"></textarea><br /><br />
      </div>

      <div class="form-group">
        <label>Diagnostico:</label>
        <select v-model="nota.diagnostico" name="Diagnostisco" id="">
          <option value="Seleccione">Seleccione</option>
          <option value="Diabétes">Diabétes</option>
          <option value="Hipertensión">Hipertensión</option>
        </select>
      </div>
      <br />

      <div class="form-group">
        <label>Tratamiento:</label>
        <select v-model="nota.tratamiento" name="Tratamiento" id="Tratamiento">
          <option value="">Seleccione</option>
          <option value="Epiprot">Epiprot</option>
          <option value="Vulcosan">Vulcosan</option>
        </select>
      </div>

      <br />
      <button class="btn" v-on:click="registroeventos">Guardar</button>
      <br /><br />
    </fieldset>
  </form>
</template>

<script>
import axios from "axios";

export default {
  name: "registroeventos",

  data: function () {
    return {
      nota: {
        usuario: "",
        profesional_en_gestion: "",
        fecha_proxima_gestion: "",
        fecha_ultima_gestion: "",
        estado_en_eps: "",
        estado_tratamiento: "",
        nota: "",
        diagnostico: "",
        tratamiento: "",
      },
      Listapacientes: [],
    };
  },

  methods: {
    registroeventos: function () {
      axios
        .post(
          "https://psp-back-01.herokuapp.com/nota/",
          this.nota
        )
        .then((respuesta) => {
          alert(respuesta.data.mensaje);
          this.nota.usuario = "";
          this.nota.profesional_en_gestion= "";
          this.nota.fecha_proxima_gestion = "";
          this.nota.fecha_ultima_gestion = "";
          this.nota.estado_en_eps = "";
          this.nota.estado_tratamiento = "";
          this.nota.nota = "";
          this.nota.tratamiento = "";
          this.nota.diagnostico = "";
          console.log(respuesta.data.mensaje);
        })
        .catch((error) => {
          alert("Error creando la nota");
          console.log(error);
        });
    },

    actualizarLista: function () {
      axios
        .get("https://psp-back-01.herokuapp.com/paciente/")
        .then((respuesta) => {
          this.Listapacientes = respuesta.data;
          console.log(respuesta.data);
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