<template>
  <div
    class="bg-image d-flex justify-content-center align-items-center"
    style="background-color: rgb(4, 40, 75)"
  >
    <v-container>
      <center><h1 style="color: white">Product</h1></center>
      <v-container class="d-flex flex-wrap">
        <v-card
          class="mx-auto mb-5"
          max-width="400"
          v-for="(i, index) in productlist"
          :key="index"
        >
          <v-img class="text-black align-end" height="350px" :src="i.imageurl">
            <v-card-title>{{ i.name }}</v-card-title>
          </v-img>

          <v-card-subtitle class="pb-0">{{ i.rightText }}</v-card-subtitle>

          <v-card-text class="text--primary">
            <div style="font-size: large">{{ i.leftText }}</div>
          </v-card-text>

          <v-card-actions>
            <v-btn color="info" text :to="'/detail/' + i.rightText"
              >detail</v-btn
            >
            <v-btn color="orange" @click="selected(i)"> Add </v-btn>
          </v-card-actions>
        </v-card>
      </v-container>

      <table class="table table-striped table-hover"></table>
      <v-container
        ><h4 class="text-danger fs-1">Total {{ total() }} Baht</h4></v-container
      >
      <v-container grid-list-xs class="white">
        <router-view :key="$route.path"></router-view>
      </v-container>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      productlist: [
        {
          name: "JUN MIZUNANI ZLC",
          imageurl:
            "https://shop.butterflyonline.com/Item%20Images/1221.main.jpg?resizeid=2&resizeh=175&resizew=175",
          rightText: "",
          leftText: "Price : 6,504",
          active: false,
          price: 6504,
        },

        {
          name: "Lin YUN JU",
          imageurl:
            "https://shop.butterflyonline.com/Item%20Images/1254.main.jpg?resizeid=2&resizeh=175&resizew=175",
          leftText: "Price : 15,900",
          active: false,
          price: 15900,
        },

        {
          name: "Vicarsra super ALC",
          imageurl:
            "https://shop.butterflyonline.com/Item%20Images/1259.main.jpg?resizeid=2&resizeh=175&resizew=175",
          rightText: "",
          leftText: "Price : 13,994",
          active: false,
          price: 13994,
        },
      ],
    };
  },
  methods: {
    selected: function (i) {
      i.active = !i.active;
    },
    total: function () {
      var sum = 0;
      this.productlist.forEach(function (i) {
        if (i.active) {
          sum += i.price;
        }
      });
      return sum;
    },
  },
};
</script>

<style>
h2 {
  color: white;
}
</style>
