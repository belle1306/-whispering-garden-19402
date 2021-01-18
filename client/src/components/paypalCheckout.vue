<template>
  <div>
    <div v-if="!paidFor">
      <h1>You have ordered - ${{ product.price }}</h1>

      <p>{{ product.description }}</p>

      <img width="400" src="https://farm3.static.flickr.com/2779/4394329911_cc0c5b17c5_o.jpg"/>
    </div>

    <div v-if="paidFor">
      <h1>Thank you for your order!</h1>

      <img src="https://media.giphy.com/media/j5QcmXoFWl4Q0/giphy.gif">
    </div>

    <div ref="paypal"></div>
  </div>
</template>

<script>

export default {
  name: "paypalCheckout",
  data: function() {
    return {
      loaded: false,
      paidFor: false,
      product: {
        price: 20,
        description: "best in town",
        img: "https://farm3.static.flickr.com/2779/4394329911_cc0c5b17c5_o.jpg"
      }
    };
  },
  mounted: function() {
    const script = document.createElement("script");
    script.src =
      "https://www.paypal.com/sdk/js?client-id=AZ3Z2XTO6lE7wMjO-JX21dTcicwBbNM_8Dz4DirX0EZ2BgyY_GZM522lRgeP6N6cEhJSzNEPhlnZkiuF"
    script.addEventListener("load", this.setLoaded);
    document.body.appendChild(script);
  },
  methods: {
    setLoaded: function() {
      this.loaded = true;
      window.paypal
        .Buttons({
          createOrder: (data, actions) => {
            return actions.order.create({
              purchase_units: [
                {
                  description: this.product.description,
                  amount: {
                    currency_code: "USD",
                    value: this.product.price
                  }
                }
              ]
            });
          },
          onApprove: async (data, actions) => {
            const order = await actions.order.capture();
            this.data;
            this.paidFor = true;
            console.log(order);
          },
          onError: err => {
            console.log(err);
          }
        })
        .render(this.$refs.paypal);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>