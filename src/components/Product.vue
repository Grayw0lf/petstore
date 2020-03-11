<template>
    <div>
      <my-header></my-header>
      <h1>This is Id {{ $route.params.id }}</h1>
      <div class="row">
        <div class="col-md-5 offset-md-0">
          <figure>
            <img class="product" :src="product.image">
          </figure>
        </div>
        <div class="col-md-6 offset-md-0 description">
          <h1>{{ product.title }}</h1>
          <p v-html="product.description"></p>
          <p class="price">
            {{ product.price }}
          </p>
          <button class="btn border rounded-lg" @click="edit">Edit Product</button>
          <router-view></router-view>
        </div>
      </div>
    </div>
</template>

<script>
    import MyHeader from "./Header";
    export default {
      name: "Product",
      components: {MyHeader},
      data() {
          return {
            product: ''
          }
      },
      methods: {
        edit() {
          this.$router.push({name: 'Edit'})
        }
      },
      created() {
          axios.get('/static/products.json')
            .then((response) => {
              this.product = response.data.products.filter(
                data => data.id == this.$route.params.id)[0];
              this.product.image = '/' + this.product.image;
            });
      }
    }
</script>

<style scoped>

</style>
