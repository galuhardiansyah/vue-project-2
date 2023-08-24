<script setup>
import Checkbox from './ui/Checkbox.vue';
</script>

<template>
  <div class="mt-5 mb-10">
    <h3 class="font-bold text-xl">Skills</h3>
     <p class="mt-1 mb-5 text-sm text-gray-400">Choose 5 of the most important skills to show your talents! Make sure they match the keyword of the job listing if applying via an online system</p>
     <div class="flex flex-row flex-wrap">
      <Checkbox :label="'Java'"/>
      <Checkbox :label="'Javascript'"/>
      <Checkbox :label="'Python'"/>
      <Checkbox :label="'Git'"/>
      <Checkbox :label="'SQL'"/>
      <Checkbox :label="'C++'"/>
      <Checkbox :label="'Typescript'"/>
      <Checkbox :label="'C#'"/>
      <Checkbox :label="'Docker'"/>
      <Checkbox :label="'PHP'"/>
      <Checkbox :label="'React'"/>
      <Checkbox :label="'MongoDB'"/>
      <Checkbox :label="'Toad'"/>
      <Checkbox :label="'HTML CSS 3'"/>
      <Checkbox :label="'MS SQL server'"/>
     </div>
    <button class="text-blue-400 font-semibold text-sm">+ Add skill</button>
  </div>
</template>