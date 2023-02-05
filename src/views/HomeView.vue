<template>
  <div class="home">
    <h1>tie</h1>
    <stripe-checkout
    ref="checkoutRef"
    mode="payment"
    :pk="publishableKey"
    :line-items="lineItems"
    :success-url="successURL"
    :cancel-url="cancelURL"
    @loading="v => loading = v"
    />

    <button @click="submit">
          PAY NOW
    </button>
 

     
  </div>
</template>

<script>
import {StripeCheckout} from '@vue-stripe/vue-stripe'
export default{
    components:{
        StripeCheckout
    },
    data(){
        this.publishablekey = "pk_test_51MX1RtAmm9i1Ud1Z6iKEJDLcCDN1ph895F6wvEySGkb0IiGSyzCnnsXM09wURb3xMJ3Souz38ESkuKX2ROwN3hpU00bBtnaf5w"

        return{
            loading:false,
            lineItems:[
                {
                    price:"price_1MY9u0Amm9i1Ud1ZlLbJnIA5",
                    quantity:1
                }
            ],
            successURL:"http://localhost:8080/success",
            cancelURL:"http://localhost:8080/error"
        }
    },
    methods:{
        submit(){
            this.$refs.checkoutRef.redirectToCheckout()
        }
    }
}

</script>
