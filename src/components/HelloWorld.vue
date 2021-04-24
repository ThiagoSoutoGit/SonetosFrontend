<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
            src="hero.png"
            class="my-3"
            contain
            height="300"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Sonetos de Terras de Ara
        </h1>

        <p class="subheading font-weight-regular">
          Sonetos escritos por Itamar Souto
          <br>
          <br>
          <br>
          <v-btn
              depressed
              color="primary"
              to="/Sonetos"
          >
            Ler alguns Sonetos
          </v-btn>
        </p>
      </v-col>

      <v-col
          class="mb-5"
          cols="12"
      >
        <h2 class="headline font-weight-bold mb-3">
          Sonetos sobre amigos, familia e o que a vida tem de bom.
        </h2>
      </v-col>
    </v-row>
    <v-row>
      <v-spacer></v-spacer>
    </v-row>
  </v-container>
</template>
