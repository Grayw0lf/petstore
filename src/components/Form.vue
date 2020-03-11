<template>
  <div>
  <my-header :cart-item-count="cartItemCount"></my-header>
  <div class="row">
    <div class="form-group col-md-6">
      <strong>First name:</strong>
      <input v-model.trim="order.firstName" class="form-control">
    </div>
    <div class="form-group col-md-6">
      <strong>Last name:</strong>
      <input v-model.trim="order.lastName" class="form-control">
    </div>
    <div class="form-group col-md-12">
      <strong>Address:</strong>
      <input v-model.trim="order.address" class="form-control">
    </div>
    <div class="form-group col-md-12">
      <strong>City:</strong>
      <input v-model.trim="order.city" class="form-control">
    </div>
    <div class="form-group col-md-2">
      <strong>State:</strong>
      <select v-model="order.state" class="form-control">
        <option disabled value="">State</option>
        <option v-for="(state, key) in states" :value="state">
          {{ key }}
        </option>
      </select>
    </div>
    <div class="form-group col-md-6 offset-md-4">
      <strong>Zip / Postal code:</strong>
      <input v-model.number="order.zip" class="form-control">
    </div>
    <div class="form-group col-md-6">
      <div class="boxes">
        <label for="gift">Ship As Gift?</label>
        <input type="checkbox" id="gift" :true-value="order.sendGift"
               :false-value="order.dontSendGift" v-model="order.gift">
      </div>
    </div>
    <div class="form-group col-md-6">
      <div class="boxes">
        <label for="home">Home</label>
        <input type="radio" id="home" :value="order.home" v-model="order.method">
        <label for="business">Business</label>
        <input type="radio" id="business" :value="order.business" v-model="order.method">
      </div>
    </div>
    <div class="form-group col-md-6">
      <button type="submit" class="btn btn-primary submit" @click="submitForm">
        Place order
      </button>
    </div>
    <div class="col-md-12 verify">
      <pre>
        First name: {{ order.firstName }}
         Last name: {{ order.lastName }}
           Address: {{ order.address }}
              City: {{ order.city }}
               Zip: {{ order.zip }}
             State: {{ order.state }}
              Gift: {{ order.gift }}
            Method: {{ order.method }}
      </pre>
    </div>
  </div>
  </div>
</template>

<script>
    import MyHeader from "./Header";
    export default {
      name: "Form",
      props: ['cartItemCount'],
      components: {MyHeader},
      data() {
        return {
          showProduct: true,
          order: {
            firstName: '',
            lastName: '',
            address: '',
            city: '',
            zip: '',
            state: '',
            method: 'Home address',
            business: 'Business address',
            home: 'Home address',
            gift: 'Send as a gift',
            sendGift: 'Send as a gift',
            dontSendGift: 'Do not send as a gift',
          },
          states: {
            AL: 'Alabama',
            AR: 'Arizona',
            CA: 'California',
            NV: 'Nevada',
          },
        }
      },
      methods: {
        submitForm() {
          alert('Submitted');
        }
      }
    }
</script>

<style scoped>

</style>
