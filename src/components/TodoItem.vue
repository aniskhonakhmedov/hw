<template>
  <div class="TodoItem">
    <div class="aboutToDo">
      <div>
        <h5>{{ item.title }}</h5>
        <i>{{ item.time }} </i>
      </div>
      <div class="X">
        <button
         style="border: none; width: fit-content; height: fit-content; background: none; filter: invert(100%);"
          width="15px"
          alt="X"
          @click="$emit('delete_todo', item.id)"
        >
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-x-circle"><circle id="circle" cx="12" cy="12" r="10"></circle><line x1="15" y1="9" x2="9" y2="15"></line><line x1="9" y1="9" x2="15" y2="15"></line></svg>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["item"],
};
</script>

<style>
</style>