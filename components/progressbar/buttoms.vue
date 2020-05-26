<template>
  <div>
    <h4>THC
    <v-progress-circular
      :size="50"
      :width="8"
      :value="value"
      color="teal"
      class="justify-right"
    >{{ value }}</v-progress-circular></h4>
    <hr>
    <p>Temperamentos
    <v-progress-linear
      background-color="#aa0061"
      color="#eedc00"
      value="45"
      :height="height"
    ></v-progress-linear></p>
    <br>
    <p>calmante - energizante
      <v-progress-linear
      color="light-blue"
      height="10"
      value="70"
      striped
    ></v-progress-linear>
    </p>
  </div>
</template>

<script>
export default {
    data: () => ({
      skill: 20,
      knowledge: 33,
      power: 78,
      height: 10,
        value: 16.5,
    }),
}
</script>
