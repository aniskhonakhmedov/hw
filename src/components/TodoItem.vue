<template>
  <div id="TodoItem">
    <div class="aboutToDo">
      <div>
        <h5>{{ parent_info.title }}</h5>
        <i>{{ parent_info.time }} {{parent_info.id}}</i>
      </div>
      <div class="X">
        <img
          src="https://cdn-icons.flaticon.com/png/512/3114/premium/3114815.png?token=exp=1642787118~hmac=95a0bc725a5bcbedcaf11b0a8fb506bb"
          width="15px"
          alt="X"
          @click="$emit('delete_todo', parent_info.id)"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["parent_info"],
};
</script>

<style>
</style>