<template>
  <div id="app">
    <Header />

    <div class="main">
      <div class="model">
        <div class="pc">
          <div :class="{ active_img: isActive }" class="img" />
        </div>
        <div class="about">
          <div class="name">Macbook Pro</div>
          <div class="color" :class="{ color: isActive }">
            {{ this.isActive ? "White" : "Space Gray" }}
          </div>
          <br />
          <h1 class="price">
            {{ "$" + first_price.toString().slice(0, 1) + ',' + first_price.toString().slice(1) }}
          </h1>
        </div>
      </div>

      <div class="buttons">
        <div class="view">
          <button
            class="white"
            :disabled="isActive"
            @click="color(true)"
            :class="{ active: isActive }"
          >
            White
          </button>
          <button
            class="space"
            :disabled="!isActive"
            @click="color(false)"
            :class="{ active: !isActive }">Space Grey</button>
        </div>
        <div class="wrap">
          <div v-for="item of data" :key="item.id" class="item">
            <button
              @click="model(item, data)"
              :class="{ active: item.isActive ? item.isActive : '' }">
              <p>{{ item.title }}</p>
              <p>{{ `${item.plus ? "+$" + `${item.plus}`  : ""}` }}</p>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";

export default {
  name: "App",
  data: () => {
    return {
      isActive: true,

      first_price: 1999,
      stay_price: 1999,

      colors: [
        {
          title: "White",
          isActive: true,
        },
        {
          title: "Space Gray",
          isActive: false,
        },
      ],

      data: [
        {
          id: "1",
          isActive: true,
          plus: 0,
          title: "512 GB SSD",
        },
        {
          id: "2",
          isActive: false,
          plus: 200,
          title: "1 TB SSD",
        },
        {
          id: "3",
          isActive: false,
          plus: 600,
          title: "2 TB SSD",
        },
        {
          isActive: false,
          id: "4",
          title: "4 TB SSD",
          plus: 1200,
        },
      ],
    };
  },

  methods: {
    color: function (bool, name) {
      this.isActive = !this.isActive;
    },
    
    model: function (cash, data) {
      for (let item of data) {
        let count = this.stay_price;
        item.isActive = false;
        cash.isActive = true;
        this.first_price = count + cash.plus;
      }
    },
  },

  components: { Header },
};
</script>

<style>
* {
  font-family: "Gilroy";
  box-sizing: border-box;
  padding: 0;
}

#app {
  font-family: "Gilroy";
  text-align: center;
  margin: 0 auto;
  width: 1000px;
  display: flex;
  align-items: center;
  flex-direction: column;
}

.wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.wrap button:hover {
  cursor: pointer;
  background-color: #007fff30;
}

.wrap button {
  display: flex;
  justify-content: space-between;
  font-weight: 800;
  width: 300px;
  border-radius: 10px;
  padding: 5px 15px;
  text-transform: uppercase;
  margin: 10px;
  background: transparent;
  transition: 0.3s ease;
  border: 2px solid #cfe7ff;
}

button:hover {
  cursor: pointer;

}

.view {
  display: flex;
  align-items: center;
  justify-content: center;
}

.view button {
    margin: 0px 10px;
  background: #cfe7ff;
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  border-radius: 10px;
  color: black;
  width: 155px;
  height: 42px;
}

.view button.active {
  color: #fff;
  background: #0071e3;
}

h1.price {
  font-weight: bold;
  font-size: 48px;
}

button.active {
  border: 2px solid #007fff;
  box-sizing: border-box;
  border-radius: 10px;
}

.model {
  display: flex;
  align-items: center;
}

.img {
  background-image: url("https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/mbp14-silver-select-202110_GEO_RU?wid=452&hei=420&fmt=jpeg&qlt=95&.v=1633657234000");
  background-position: center;
  background-size: cover;
  width: 300px;
  height: 300px;
}
.active_img {
  background-image: url("https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/mbp14-spacegray-select-202110_GEO_RU?wid=452&hei=420&fmt=jpeg&qlt=95&.v=1633657385000");
}

.name {
  font-size: 48px;
  font-weight: bold;
}

.color {
  font-weight: bold;
  font-size: 24px;
  color: #0071e3;
}

.about {
  margin-left: 70px;
  text-align: left;
}
</style>
