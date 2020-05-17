<template>
  <div class="footer">
    <div class="columns container">
      <div class="column">
        <h3 class="white-text">Síguenos</h3>
          <a href="#"><i style="font-size: 38px; color: white;" class="fa fa-facebook-square"></i></a> &nbsp;&nbsp;&nbsp;
          <a href="#"><i style="font-size: 38px; color: white;" class="fa fa-twitter-square"></i></a>&nbsp;&nbsp;&nbsp;
          <a href="#"><i style="font-size: 38px; color: white;" class="fa fa-google-plus-square"></i></a>
      </div>
      <div class="column has-text-right">
        <h3 class="white-text">Categorias</h3>
        <ul>
          <li><a class="grey-text text-lighten-3" href="#!">Categoria</a></li>
          <li><a class="grey-text text-lighten-3" href="#!">Categoria</a></li>
          <li><a class="grey-text text-lighten-3" href="#!">Categoria</a></li>
          <li><a class="grey-text text-lighten-3" href="#!">Categoria</a></li>
        </ul>
      </div>
      <div class="column has-text-right">
        <h3 class="white-text">Populares</h3>
          <ul>
            <li><a class="grey-text text-lighten-3" href="#!">Cepa</a></li>
            <li><a class="grey-text text-lighten-3" href="#!">Cepa</a></li>
            <li><a class="grey-text text-lighten-3" href="#!">Cepa</a></li>
            <li><a class="grey-text text-lighten-3" href="#!">Cepa</a></li>
          </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VmFooter',
}
</script>

<style lang="scss" scoped>
 .footer {
   background: #43a047;
   color: black;
 }
 a, h3 {
   color: white;
 }
</style>
