<template>
  <div id="AddForm">
      <input type="text" v-model="inputValue" />
      <button @click="ChildFunction">Add</button>
  </div>
</template>

<script>
export default {
  name: "AddForm",

  data(){
    return{
      inputValue: "",
    };
  },

  methods:{
    ChildFunction: function(){
      this.$emit("ShareMyScreams", this.inputValue)
    },
  },
};
</script>

<style>
input{
  margin-right: 8px;
  width: 320px;
  height: 42px;
  border-radius: 10px;
  border: 2px solid #007FFF;
}

button{
  width: 155px;
  height: 42px;
  border-radius: 10px;
  color: #fff;
  background: #0071E3;
  border: none;
}
</style>