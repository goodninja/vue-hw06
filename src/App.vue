<template>
  <div id="app">
    <HeaderComp />
    <div class="button__container center">
      <button
        class="button__checked"
        :class="{ 'tag-clicked': tag === filterItem }"
        @click="clickTag(tag)"
        v-for="tag in getTags"
        :key="tag.id"
      >
        {{ tag }}
      </button>
    </div>
    <CardComp :cards="filterCards" />
    <FooterComp />
  </div>
</template>

<script>
import CardComp from "./components/CardComp.vue";
import FooterComp from "./components/FooterComp.vue";
import HeaderComp from "./components/HeaderComp.vue";

export default {
  name: "App",
  data() {
    return {
      cards: [
        {
          title: "Minimal Bedroom",
          text: "Decor / Artchitecture",
          tag: "BedRoom",
          img: "img/card_prod.png",
        },
        {
          title: "Minimal Bedroom",
          text: "Decor / Artchitecture",
          tag: "BedRoom",
          img: "img/card_prod.png",
        },

        {
          title: "Classic Minimal Bedroom",
          text: "Decor / Artchitecture",
          tag: "BedRoom",
          img: "img/card_prod.png",
        },
        {
          title: "Modern Bedroom",
          text: "Decor / Artchitecture",
          tag: "BedRoom",
          img: "img/card_prod.png",
        },
        {
          title: "Classic Minimal Bathroom",
          text: "Decor / Artchitecture",
          tag: "Bathroom",
          img: "img/card_prod2.png",
        },
        {
          title: "Modern Bathroom",
          text: "Decor / Artchitecture",
          tag: "Bathroom",
          img: "img/card_prod2.png",
        },
        {
          title: "Minimal Bathroom",
          text: "Decor / Artchitecture",
          tag: "Bathroom",
          img: "img/card_prod2.png",
        },
        {
          title: "Minimal Bathroom",
          text: "Decor / Artchitecture",
          tag: "Bathroom",
          img: "img/card_prod2.png",
        },
        {
          title: "Minimal Kitchen",
          text: "Decor / Artchitecture",
          tag: "Kitchen",
          img: "img/card_prod3.png",
        },
        {
          title: "Minimal Kitchen",
          text: "Decor / Artchitecture",
          tag: "Kitchen",
          img: "img/card_prod3.png",
        },
        {
          title: "Classic Minimal Kitchen",
          text: "Decor / Artchitecture",
          tag: "Kitchen",
          img: "img/card_prod4.png",
        },
        {
          title: "Classic Minimal Kitchen",
          text: "Decor / Artchitecture",
          tag: "Kitchen",
          img: "img/card_prod4.png",
        },
      ],
      filterItem: "Kitchen",
    };
  },
  components: {
    CardComp,
    HeaderComp,
    FooterComp,
  },
  computed: {
    getTags() {
      let tags = [];
      this.cards.forEach((el) => {
        tags.push(el.tag);
      });
      return new Set(tags);
    },
    filterCards() {
      return this.cards.filter((card) => {
        return card.tag.includes(this.filterItem);
      });
    },
  },
  methods: {
    clickTag(tag) {
      this.filterItem = tag;
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: "Jost", sans-serif;
  font-family: "DM Serif Display", serif;

  .center {
    padding-left: calc(50% - (1200px / 2));
    padding-right: calc(50% - (1200px / 2));
  }

  a {
    text-decoration: none;
  }
  .button__checked {
    border: none;
    padding: 26px 66px;
    color: #292f36;
    text-align: center;
    font-family: Jost;
    font-size: 18px;
    font-style: normal;
    font-weight: 600;
    line-height: 125%; 
    letter-spacing: 0.36px;
    border-radius: 18px;
    background: #ffffff;
    &:hover {
      color: #fff;
      background: #cda274;
    }
  }
}
</style>
