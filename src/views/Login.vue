<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <br />
        <br />
        <br />
        <br />
        <br /><br /><br /><br /><br /><br />
        <h1>Ingreso</h1><br />

        <v-btn outlined color="yellow" @click="ingresar">Ingreso</v-btn>
        <br /><br />
        <br />
        <v-btn outlined color="blue" @click="mapa">Mapa</v-btn>
        <br /><br />
        <br />
        <v-btn outlined color="green" @click="datos">Tabla</v-btn>
        <br /><br />
        <br />
        <v-btn outlined color="green" @click="traerDatosApi">trer datos desde api</v-btn>
        <br>
<br> 
        <v-btn   elevation="3"    outlined   x-large @click="mapa" >mapa</v-btn>
      </v-col>
      {{ comentarios }}
      
    </v-row>

    <template>
  <v-stepper v-model="e1">
    <v-stepper-header>
      <v-stepper-step
        :complete="e1 > 1"
        step="1"
      >
        Eleccion de perfil
      </v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step
        :complete="e1 > 2"
        step="2"
      >
        Carga de datos
      </v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step step="3">
        Confirmacion
      </v-stepper-step>
    </v-stepper-header>

    <v-stepper-items>
      <v-stepper-content step="1">
        <v-card
          class="mb-12"
          color="grey lighten-1"
          height="200px"
        ></v-card>

        <v-btn
          color="primary"
          @click="e1 = 2"
        >
          Continuar
        </v-btn>

        <v-btn text>
          Cancelar
        </v-btn>
      </v-stepper-content>

      <v-stepper-content step="2">
        <v-card
          class="mb-12"
          color="grey lighten-1"
          height="200px"
        ></v-card>

        <v-btn
          color="primary"
          @click="e1 = 3"
        >
          Continuar
        </v-btn>

        <v-btn text>
          Cancelar
        </v-btn>
      </v-stepper-content>

      <v-stepper-content step="3">
        <v-card
          class="mb-12"
          color="grey lighten-1"
          height="200px"
        ></v-card>

        <v-btn
          color="primary"
          @click="e1 = 1"
        >
          Continuar
        </v-btn>

        <v-btn text>
          Cancelar
        </v-btn>
      </v-stepper-content>
    </v-stepper-items>
  </v-stepper>
</template>
  </v-container>
</template>
<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Login",
  data: () => ({
    comentarios: [],
  }),
  methods: {
    traerDatosApi(){
      fetch('https://jsonplaceholder.typicode.com/comments')
      .then(response => response.json())
      .then(json => (this.comentarios=json))
      .then(json => console.log(json))
    },
    mapa() {
      this.$router.push("/about");
      this.$store.state.btnLogin = true;
    },
    ingresar() {
      this.$router.push("/");
      this.$store.state.btnLogin = true;
    },
    datos() {
      this.$router.push("/datos");
      this.$store.state.btnLogin = true;
    },
  },
};
</script>