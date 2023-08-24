<script setup>
const props = defineProps({
  label: {
    type:String
  }
})

</script>

<template>
  <label class="cursor-pointer mr-3 mb-3">
    <input type="checkbox" :name="props.label" :id="'id' + props.label" class="hidden peer" />
    <p class="peer-checked:bg-blue-500 bg-gray-100 peer-checked:text-white rounded-sm py-1 px-2">{{ props.label }}</p>
  </label>
</template>

<style scoped>

 input:checked + p:after {
        content: " ✓ ";
    }
  input:not(:checked) + p:after{
    content: " + ";
  }

</style>