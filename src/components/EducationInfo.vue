<script setup>
import { ref, reactive } from 'vue';
import Editor from '@tinymce/tinymce-vue'
import Input from './ui/Input.vue';

const isForm = ref(false)
const educations = reactive([{
  school: '',
  degree: '',
  startDate: '',
  endDate: '',
  city: '',
  toggle: false
}])

const showForm = () => {
  isForm.value = true
}
const toogleForm = (index) => {
  if (index === 0 && !(educations[index].school && educations[index].degree)) {
    isForm.value = false
    // educations[index].toggle = false
  } else {
    educations[index].toggle = !educations[index].toggle
  }
}

const getDate2 = (date) => {
  let options1 = { year: 'numeric', month: 'short' };
  return new Date(date).toLocaleDateString("id-ID", options1)
}

const addRow = () => {
  educations.push(
    {
      jobTitle: '',
      employer: '',
      startDate: '',
      endDate: '',
      city: '',
      toggle: false
    }
  )
}
</script>

<template>
  <div class="mt-5 mb-10">
    <h3 class="font-bold text-xl">Education</h3>
    <p class="mt-1 mb-5 text-sm text-gray-400">A varied education on your resume sums up the value that your learnings and background will bring to job</p>
    <div class="mt-2 mb-5">
      <button class="text-blue-400 font-semibold text-sm" @click="showForm" v-if="!isForm">+ Add education</button>
      <div class="border rounded-sm py-4 px-6 mb-4" v-else v-for="(education, index) in educations" :key="index">
        <div class="flex flex-row justify-between mb-4">
          <div class="flex flex-col">
            <p class="font-semibold mt-3">{{ education.school && education.degree ? `${education.degree} at ${education.school}` : '(not specified)' }}</p>
            <p class="text-gray-400 text-[15px]" v-show="education.startDate && education.endDate">{{ `${getDate2(education.startDate)} - ${getDate2(education.endDate)}` }}</p>
          </div>
      
          <button class="p-3" @click="toogleForm(index)">
            <svg fill="#000000" width="30px" height="30px" :class="{ 'rotate-180 transition-all ease-out duration-200': education.toggle }" viewBox="-5 -7.5 24 24" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMinYMin" class="jam jam-chevron-up"><path d='M7.071 2.828l-4.95 4.95A1 1 0 0 1 .707 6.364L6.364.707a1 1 0 0 1 1.414 0l5.657 5.657a1 1 0 0 1-1.414 1.414l-4.95-4.95z' /></svg>
          </button>
        </div>
        <div v-if="!education.toggle">
          <div class="flex flex-row justify-start">
            <Input :label="'School'" :wInput="'w-full'" class="w-[48%] mr-8" v-model="education.school" />
            <Input :label="'Degree'" :wInput="'w-full'" class="grow" v-model="education.degree" />
          </div>
          <div class="flex flex-row justify-between">
            <div class="flex flex-col w-1/2 mt-2 mr-3">
              <label class="text-gray-400 text-xs flex  w-flex-row">Start & End Date</label>
              <div class="flex flex-row justify-start">
                  <Input :type="'date'" :maxDate="Date.now()" :wInput="'w-full'" class=" grow" v-model="education.startDate"/>
                  <Input :type="'date'" :maxDate="Date.now()" :wInput="'w-full'" class="grow mx-5" v-model="education.endDate"/>
              </div>   
            </div>
            <Input :label="'City'" :wInput="'w-full'" class="grow" v-model="education.city" />
          </div>
          <div class="mt-6">
            <p class="text-gray-400 text-xs">Description</p>
            <Editor />
          </div>  
        </div> 
      </div>
    </div>
    <button class="text-blue-400 font-semibold text-sm" v-if="isForm" @click="addRow">+ Add One More education</button>
  </div>
</template>