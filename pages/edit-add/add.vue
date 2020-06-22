<template>
<div class="col-sm-12 justify-center">
    <v-row align="center">
        <div class="col-md-7">
        <v-file-input
        label="Subir imagen"
        filled
        prepend-icon="mdi-camera"
    ></v-file-input>
    </div>
    <v-form
      ref="form"
      v-model="valid"
      :lazy-validation="lazy"
    >
      <v-text-field
        v-model="name"
        :counter="50"
        :rules="nameRules"
        label="Nombre"
        required
      ></v-text-field>

      <v-text-field
        v-model="email"
        :rules="emailRules"
        label="THC"
        required
      ></v-text-field>

      <v-text-field
        v-model="email"
        :rules="nameRules"
        label="descripción"
        required
      ></v-text-field>
      <h2 style="color: green;">Terpenos</h2>
       
           <v-col>
            <v-checkbox
              v-model="ex4"
              label="Picante"
              color="red"
              value="red"
              hide-details
            ></v-checkbox>
            <v-checkbox
              v-model="ex4"
              label="Acido"
              color="yellow"
              value="red darken-3"
              hide-details
            ></v-checkbox>
            <v-checkbox
              v-model="ex4"
              label="Herbario"
              color="indigo"
              value="indigo"
              hide-details
            ></v-checkbox>
            <v-checkbox
              v-model="ex4"
              label="Frutal"
              color="indigo darken-3"
              value="indigo darken-3"
              hide-details
            ></v-checkbox>
            <v-checkbox
              v-model="ex4"
              label="Menta"
              color="orange"
              value="orange"
              hide-details
            ></v-checkbox>
          </v-col>
      <v-btn
        :disabled="Aceptar"
        color="success"
        class="mr-4"
        @click="Aceptar"
      >
        Aceptar
      </v-btn>

      <v-btn
        color="error"
        class="mr-4"
        @click="reset"
      >
        Cancelar
      </v-btn>

      <v-btn
        color="warning"
        @click="resetValidation"
      >
        Resetear
      </v-btn>
    </v-form>
  </v-row>
</div>
</template>

<script>
export default {
  name: 'add',
    data: () => ({
        ex4: ['red', 'indigo', 'orange', 'primary', 'secondary', 'success', 'info', 'warning', 'error', 'red darken-3', 'indigo darken-3', 'orange darken-3'],
      valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 50) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      select: null,
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4',
      ],
      checkbox: false,
    }),

    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
}
</script>

<style lang="scss" scoped>

.v-file-input{
    weight: 15 px;
}
  hr{
    border: 1px solid green;
  }
  .card-content {
    padding: 15px 10px 15px 0;

    &__text {
      margin: 15px 0;
    }
    &__reviews {
      display: inline-block;
      width: 100%;
      margin-bottom: 10px;
    }
  }
</style>

