<template>
    <div class="row">
     <div class="column">
        <div class="blue-column">
    <img class="resize"  v-bind:src="list.gallery[0].main"/>
    </div>
</div>
  
<div class="column" >
    <div class="green-column" >
      <p>  <span class="readytoship" style="" v-if="list.shipping.props.in_stock">Ready to Ship</span>
         <span v-else>Ready to Ship <v-icon>nice</v-icon></span>
        <span  class="instock" >  In Stock </span>
        <span  class="instock" >  Fast Dispatch </span>
     </p>

   <p>
    <span class="gps">{{list.name}}</span>
    <span class="label"> {{list.tags[0]}}</span>
    </p>

     <p>
     <span class="rev">{{list.reviews.rating}} </span>
     <span class="reviews">{{list.reviews.count}} Reviews   </span>
     <span class="buyers">{{list.reviews.total_buyers}} Buyers</span>
     </p>
     <hr>
   
        <p style="padding-right:300px">
            <span class="r-78-50-r-895-31"><strong> {{list.options.battery_accessories.price.currency.symbol}}{{list.options.battery_accessories.price.value}} - {{list.options["4k"].price.currency.symbol}} {{list.options["4k"].price.value}}</strong></span>
            
                <span class="option"> /option</span>
                <span class="options"> 2 options </span>
                <span class="min-order">(Min. Order)</span>
                </p>

         <p class="r-98-12-r-1-119-14" style="text-decoration:line-through;">{{list.options.battery_accessories.price.currency.symbol}}{{list.options.battery_accessories.old_price.value}} - {{list.options["4k"].price.currency.symbol}}{{list.options["4k"].old_price.value}}</p>
         <hr>

        <div class="foreground" >
       <img src="/src/assets/Logo.png">
        <span class="free-shipping-up" >  . Free Shipping(Up to $40)    </span>
        <span class="free-shipping-up"> . On time delivery gauranteed </span>
        </div>

   <p>
       <span class="off">{{list.discount.amount}} OFF</span>
       <span> Discount ends in {{list.discount.end_date}}</span>
       </p>

        <p>
            <span style="padding-right:240px ">Options:</span>
                <span class="product" style="padding-right:20px"> {{list.options["1080p"].label}}</span>
                <span class="product"  style="padding-right:10px"> {{list.options["1080p"].price.currency.symbol}}{{list.options["1080p"].price.value}}</span>
                <button class="button"  @click="removeFromCart" v-bind:disabled="cart<1"> - </button>
                <input class="input" style=" color: #999999; font-family: Roboto; font-size: 14px; line-height: 16px; width: 80px; text-align: center" v-model="cart" v-on:input="$emit('input', cart)"  min="0" oninput="validity.valid||(value='')">{{cart}}
      <button class="button" v-on:click="addToCart"> +</button>
         </p> 
   
        <p style="padding-right:10px"> 
            <span class="product" style="padding-right:70px">{{list.options["4k"].label}}</span>
            <span class="product"  style="padding-right:10px">{{list.options["4k"].price.currency.symbol}}{{list.options["4k"].price.value}}</span>
                <button class="button" style="" @click="removeFromCart2" v-bind:disabled="cart2<1"> - </button>
                <input v-model="cart2" v-on:input="$emit('input', cart2)"  class="input" style=" color: #999999; font-family: Roboto; font-size: 14px; line-height: 16px;  width: 80px; text-align: center"  min="0" oninput="validity.valid||(value='')">{{cart2}}
      <button class="button"  v-on:click="addToCart2"> +</button>
        </p> 
        
        <p>
            <span class="product"> {{list.options.battery_accessories.label}}</span> 
            <span class="product"> {{list.options.battery_accessories.price.currency.symbol}}{{list.options.battery_accessories.price.value}}</span> 
            
     <button class="button" @click="removeFromCart3" v-bind:disabled="cart3<1"> - </button>
     
                <input class="input" style=" color: #999999; font-family: Roboto; font-size: 14px; line-height: 16px; width: 80px;  width: 80px; height: 40px; text-align: center" v-model="cart3" v-on:input="$emit('input', cart3)"  min="0" oninput="validity.valid||(value='')"> {{cart3}}
      <button class="button" v-on:click="addToCart3" > +</button>
              
            </p>
        <p class="protects-your-alibab "><strong>Trade Asssuarance </strong>protects your alibaba.com orders</p>
        <p class="protects-your-alibab ">payments:</p>
        <p class="protects-your-alibab ">Alibaba.com Logistics   inspection solutions</p>
     </div>
</div>
<div class="column">
    <div class="orange-column">
        <div class="card">
 
 
<v-card   class="container">
    <v-card-text class="ship-to-south-africa">Ship to {{list.shipping.method.country}}</v-card-text>
     <v-card-text>{{list.shipping.method.cost.currency.symbol}}</v-card-text>
      <v-card-text>{{list.shipping.method.cost.value}}</v-card-text><br>
        <v-card-text class="ship-to-south-africa">By {{list.shipping.method.title}}</v-card-text><br><br>
                <v-card-text class="ship-to-south-africa">Lead time {{list.shipping.lead_time.value}}</v-card-text><br><br>
        <v-card-text class="ship-to-south-africa">Shipping time {{list.shipping.method.shipping_time.value}}</v-card-text><br><br>
<v-btn class="login-label">login to purchase</v-btn><br>
<v-btn class="contact">contact the supplier</v-btn>
</v-card>
 </div>
    </div>
</div>
    </div>
    
</template>
<script>
import Vue from 'vue';
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios,axios)
export default {
    name: "AssessmentData",
    data(){
 return {list:undefined, cart: 0,cart2: 0,cart3: 0}
    },

   mounted(){
       
      Vue.axios.get('https://fe-assignment.vaimo.net/')
       .then((resp)=>{
           this.list=resp.data.product
           console.warn(resp.data.product)
       }
       )
   },
   
methods: {
    addToCart() {
      this.cart += 1
    },

    removeFromCart() {
      this.cart -= 1
    },
       addToCart2() {
      this.cart2 += 1
    },

    removeFromCart2() {
      this.cart2 -= 1
    },
       addToCart3() {
      this.cart3 += 1
    },

    removeFromCart3() {
      this.cart3 -= 1
    },
    totalcart1(){
        this.cart * this.list.options["4k"].price
    },
    totalcar2(){
        this.cart * this.list.options["1080p"].price
    },
    totalcart3(){
        this.cart * this.list.options.battery_accesories.price
    }
   }
}
  

</script>
<style lang="scss">
@import "../assets/variables.scss";
</style>