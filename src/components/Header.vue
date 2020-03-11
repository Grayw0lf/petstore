<template>
<div>
<header>
  <nav class="jumbotron navbar">
    <div class="navbar-header">
      <h1>
        <router-link :to="{name: 'iMain'}">{{ sitename }}</router-link>
      </h1>
    </div>
    <div class="nav navbar-nav cart">
      <router-link active-class="active" tag="button"
                   class="btn border border-success rounded-lg" :to="{name: 'Form'}">
        <span class="fa fa-shopping-cart"> {{ cartItemCount}}</span> Checkout
      </router-link>
    </div>
  </nav>
</header>
</div>
</template>

<script>
    export default {
      name: "my-header",
      data() {
        return {
          sitename: 'Vue.js Pet Depot'
        }
      },
      props: ['cartItemCount'],
      methods: {
        showCheckout() {
          this.$router.push({name: 'Form'});
        }
      }
    }
</script>

<style scoped>
  a {
    text-decoration: none;
    color: black;
  }

  button.router-link-exact-active {
    color: blue;
  }
</style>
