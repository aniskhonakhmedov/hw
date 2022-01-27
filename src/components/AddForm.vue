<template>
  <div id="AddForm">
    <form>
      <input
        type="text"
        placeholder="Введите свои задачи"
        :class="{ active: this.isActive, greenBorder: this.isTurnOn }"
        v-model="inputValue"
      />
      <button @click="ChildFunction" class="btn-primary btn-round btn-marquee">
        <span data-text="Marquee">Add</span>
      </button>
    </form>
    <p class="hide" :class="{ active: this.isActive }">
      Введите пожалуйста текст
    </p>
  </div>
</template>

<script>
export default {
  name: "AddForm",

  data() {
    return {
      isTurnOn: false,
      isActive: false,
      inputValue: "",
    };
  },

  methods: {
    ChildFunction: function () {
      event.preventDefault();
      if (this.inputValue === "") {
        this.isActive = true;
      } else {
        this.isTurnOn = true;
        this.isActive = false;
        this.$emit("ShareMyScreams", this.inputValue);
      }
    },
  },
};
</script>

<style>
.btn-marquee {
  font-weight: 600;
  border: none;
  overflow: hidden;
  transition: 0.3s;
}

span {
  display: block;
  padding: 0 20px;
  animation: move-left 2s linear infinite;
}

span::after {
        position: absolute;
        content: attr(data-text);
        top: 0;
        left: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 100%;
}
.btn-marquee:hover {
  transform: scale(1.1);
}

.hide {
  transform: translateX(150px);
  opacity: 0;
  font-size: 20px;
  font-weight: bold;
  transition: 0.3s ease;
  color: red;
}

.hide.active {
  opacity: 1;
  transform: translateX(0);
}

.greenBorder {
  border: 1px solid green;
}

input.active {
  border: 2px solid red;
}

input {
  margin-right: 8px;
  width: 320px;
  height: 42px;
  border-radius: 10px;
  border: 2px solid #007fff;
}

button {
  width: 155px;
  height: 42px;
  border-radius: 10px;
  color: #fff;
  background: #0071e3;
  border: none;
}
</style>