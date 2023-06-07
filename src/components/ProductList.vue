<template lang="pug">
.container 
    h1 Shopping list
      ProductInput(
        v-model="searchText"
        @findProduct="findProduct(searchText)"
        )
      ul(class="list-default flex")
        li(
          v-for="(product, index) in products"
          :key="index"
        )  
          ProductCard(
            :title='product.title'
            :price='product.price'
            :imgUrl='product.imgUrl'
            :count='product.count'
            @addToBascked='addToBascked(product.title)'
          )
          SlotRefs
          

</template>

<script>
import ProductCard from "./ProductCard";
import ProductInput from "./ProductInput";
import SlotRefs from "./SlotRefs";

export default {
  name: "ProductList",
  components: { ProductCard, ProductInput, SlotRefs },
  props: [],
  data() {
    return {
      searchText: "",
      products: [
        {
          title: "Стол Jim",
          price: 133333,
          imgUrl:
            "data:image/jpeg;base64,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",
          count: 30,
        },
        {
          title: "Стол Monako",
          price: 17199,
          imgUrl:
            "data:image/jpeg;base64,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qoqDu0uq433W/vSRcjGUujiMMTsIrJr7CAj27gCEPvGBakREBERAREQEREBERArnllytzeESgD0qz6x/h07MfxGn6ytMysm/SsZQpEXUvpv3c2nSYHwNtH3hLF5VM1a2J0cRSJbm00TT0bkAFmLAdt7i9tY0Rt7KxzVyrWwmKR1YqQCrA61ZTYlSO0GwOru1GB6aiafIeXaeJS69FgLshOseI718fO03EBKv5asZanhaN+tUaodyLoC/GofKWhKL5WMbp5QK31UqaJ7zXdvR18oEbzfwXP4rD0iLh6qKw700gX/CGnpiUZyUYLTygrEaqVN3v3M1kUb7O3lLzgIiICIiAiIgIiICIiAiIgJirUVdSrKGU7QQCDvBmWIFdZxcmqOTUwjGk+3RudG/8p2r+9kh2JxONwjaGJpFgNjW17ww1N+9cvaYMThkqKVdVdTtDAEesCis5MrfS6CHT0zTJIDddVa2kDfWRcL3zo5h5T+j4/DuTZXfmn9mr0BfwDlG92Wblzk1w9U6VBjRbutpKfM3E6OSOSikjaWIrGqPsoGp7ukr3gWXERAREQEREBERAREQErzPbMJa16+GULU2tTFgHO269it4bDt1G5NhxAozJGMdGFiyOht2qysNRBB2do8x3yzs3s5FrWSpZamwHYr7u5vDy7hgzrzTTE/2tIiniANTbFe31alvLS2jVtsJAKbsrNTqKUqJqdG271718R+hNF1zzTnBjOfxWIq3uHquVP8AKGIT8IWWimd7U8NWFS7MKbc2+0htEhA/frt0tvf3yn1WQWvyM4K1PE1vtOtMbqaljbeag+7LOkX5OsFzWTsOO11NU+POsXX8JUcJKICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICaHOXNyni019CqvUqqOkp7j9pfDysZvogUNnRSrUFajXXRa46Q6jpfrKe3s1fDZIxhqD1HVEUs7EBQBc3JsDq7LnbPSWUslUMQFFeklQKbqHUNY+F5ywWTqNEEUaVOmDtCIqA79Ea4GXC0AiIi7EVVG5QAPQTPEQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQP//Z",
          count: 20,
        },
        {
          title: "Стол с двумя ящиками Кварт ",
          price: 10999,
          imgUrl:
            "https://hoff.ru/upload/iblock/1cc/1ccb33b50e3e9cfa08629bf455e41855.jpg",
          count: 23,
        },
      ],
    };
  },

  methods: {
    addToBascked(title) {
      console.log(title);
    },
    findProduct(text) {
      console.log(`загрузить товар ${text}`);
      this.products.map((n) => console.log(n.title));
    },
  },
};
</script>

<style lang="scss" scoped>
.flex {
  display: flex;
  align-items: center;
  justify-content: center;
}
li {
  margin-right: 20px;
  list-style: none;
}
.top-information {
  align-items: center;
  h1 {
    margin-bottom: 0;
  }
  button {
    background-color: rgb(221, 56, 56);
    color: #fff;
    border: none;
    border-radius: 4px;
    padding: 8px 14px;
    display: block;
    cursor: pointer;
    margin-left: 10px;
  }
  margin-bottom: 22px;
}
</style>
