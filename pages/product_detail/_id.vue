<template>
  <div class="section">
    <div class="card is-clearfix columns">
        <figure class="card-image is-480x480 column is-one-thirds">
          <img src="../../static/cepas/mini/buba.png" alt="Placeholder image">
        </figure>
        <div class="card-content column is-two-thirds">
          <div class="card-content__title">
            <h1 class="title is-4">{{ product.title }}
              <button class="button is-small" :title="removeFromFavouriteLabel" v-show="product.isFavourite" @click="removeFromFavourite(product.id)">
                <span class="icon is-small">
                  <i class="fa fa-heart"></i>
                </span>
              </button>
              <button class="button is-small" :title="addToFavouriteLabel" v-show="!product.isFavourite" @click="saveToFavorite(product.id)">
                <span class="icon is-small">
                  <i class="fa fa-heart-o"></i>
                </span>
              </button>
            </h1>
            <hr>
          </div>
          <caracteristicas></caracteristicas>
          <div class="card-content__text">
            <p>
            {{ product.description }}
            </p>
          </div>
          <div class="card-content__ratings" v-if="product.rating === 1">
            <i class="fa fa-star"></i>
          </div>
          <div class="card-content__ratings" v-else-if="product.rating === 2">
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
          </div>
          <div class="card-content__ratings" v-else-if="product.rating === 3">
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
          </div>
          <div class="card-content__ratings" v-else-if="product.rating === 4">
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
          </div>
          <div class="card-content__ratings" v-else-if="product.rating === 5">
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
          </div>
          <div class="card-content__reviews">
            <div class="is-pulled-left">
              <p><strong>{{ product.reviews > 0 ? `${product.reviews} Reviews` : 'No reviews' }}</strong></p>
            </div>
            <!--<div class="select is-rounded is-small is-pulled-right">
              <select @change="onSelectQuantity(product.id)" v-model="selected">
                <option v-for="quantity in quantityArray" :value="quantity">{{ quantity }}</option>
              </select>
            </div>-->
          </div>
          <v-rating
      v-model="rating"
      background-color="orange lighten-3"
      color="orange"
    ></v-rating>
          <!--<div class="card-content__price is-pulled-left">
            <span class="title is-3"><strong>{{ product.price }}&euro;</strong></span>
          </div>-->
          <!--<div class="card-content__btn is-pulled-right">
            <button class="button is-primary" v-if="!isAddedBtn" @click="addToCart(product.id)">{{ addToCartLabel }}</button>
            <button class="button is-text" v-if="isAddedBtn" @click="removeFromCart(product.id)">{{ removeFromCartLabel }}</button>
          </div>-->
      </div>
    </div>
    <div>
      <h2>efectos</h2>
      <v-col cols="4">
        <h3>Relajacion</h3>
        <v-progress-linear
      color="light-green darken-4"
      height="10"
      value="63"
      striped
    ></v-progress-linear>
    <h3>Sueño</h3>
    <v-progress-linear
      color="light-green darken-4"
      height="10"
      value="52"
      striped
    ></v-progress-linear>
    <h3>Felicidad</h3>
    <v-progress-linear
      color="light-green darken-4"
      height="10"
      value="51"
      striped
    ></v-progress-linear>
      </v-col>
      <v-col cols="4">
        <h3>Estres</h3>
        <v-progress-linear
      color="light-green darken-4"
      height="10"
      value="39"
      striped
    ></v-progress-linear>
    <h3>Miedo</h3>
    <v-progress-linear
      color="light-green darken-4"
      height="10"
      value="36"
      striped
    ></v-progress-linear>
    <h3>Insomnio</h3>
    <v-progress-linear
      color="light-green darken-4"
      height="10"
      value="32"
      striped
    ></v-progress-linear>
      </v-col>
      <v-col cols="4">
        <h3>Salivacion</h3>
        <v-progress-linear
      color="light-green darken-4"
      height="10"
      value="38"
      striped
    ></v-progress-linear>
    <h3>Ojos llorosos</h3>
    <v-progress-linear
      color="light-green darken-4"
      height="10"
      value="21"
      striped
    ></v-progress-linear>
    <h3>Paranoia</h3>
    <v-progress-linear
      color="light-green darken-4"
      height="10"
      value="7"
      striped
    ></v-progress-linear>
      </v-col>
    </div>
  </div>

</template>

<script>
  import caracteristicas from '@/components/progressbar/caracteristicas';

export default {
  name: 'product_detail-id',


  validate ({ params }) {
    return /^\d+$/.test(params.id)
  },
  
  data () {
    return {
      rating: product.rating,
      addToFavouriteLabel: 'Add to favourite',
      removeFromFavouriteLabel: 'Remove from favourite',
      product: {},
      selected: 1,
      quantityArray: []
    };
  },

  components: {
    caracteristicas
  },

  mounted () {
    this.product = this.$store.getters.getProductById(this.$route.params.id);
    this.selected = this.product.quantity;

    for (let i = 1; i <= 20; i++) {
      this.quantityArray.push(i);
    }
  },

  computed: {
    isAddedBtn () {
      return this.product.isAddedBtn;
    }
  },

  methods: {
    addToCart (id) {
      let data = {
        id: id,
        status: true
      }
      this.$store.commit('addToCart', id);
      this.$store.commit('setAddedBtn', data);
    },
    removeFromCart (id) {
      let data = {
        id: id,
        status: false
      }
      this.$store.commit('removeFromCart', id);
      this.$store.commit('setAddedBtn', data);
    },
    onSelectQuantity (id) {
      let data = {
        id: id,
        quantity: this.selected
      }
      this.$store.commit('quantity', data);
    },
    saveToFavorite (id) {
      let isUserLogged = this.$store.state.userInfo.isLoggedIn;

      if (isUserLogged) {
        this.$store.commit('addToFavourite', id);
      } else {
        this.$store.commit('showLoginModal', true);
      }
    },
    removeFromFavourite (id) {
      this.$store.commit('removeFromFavourite', id);
    }
  }
};
</script>

<style lang="scss" scoped>
.title{
  font-size: 35px;
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

