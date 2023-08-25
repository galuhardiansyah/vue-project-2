<script setup>
import Checkbox from './ui/Checkbox.vue';
import { ref, reactive } from 'vue';
import Input from './ui/Input.vue';

const isForm = ref(false)
const checkBoxLabel = reactive([
  'Java', 'Javascript', 'Python', 'Git', 'SQL', 'C++', 'Typescript', 'C#', 'Docker', 'PHP', 'React', 'MongoDB', 'Toad', 'HTML CSS 3', 'MS SQL Server'
])
const skillExp = reactive([
  {
    name: 'Basic',
    value: 'Basic'
  },
  {
    name: 'Medium',
    value: 'Medium'
  },
  {
    name: 'Skillful',
    value: 'Skillful'
  },
  {
    name: 'Experienced',
    value: 'Experienced'
  },
  {
    name: 'Expert',
    value: 'Expert'
  }
],)
const skills = reactive([{
  skill: '',
  toggle: false,
  picked: ''
}])

const showForm = () => {
  isForm.value = true
}
const toogleForm = (index) => {
  if (index === 0 && !skills[index].skill) {
    isForm.value = false
    // skills[index].toggle = false
  } else {
    skills[index].toggle = !skills[index].toggle
  }
}

const addRow = () => {
  skills.push(
    {
      skill: '',
      toggle: false,
      picked: ''
    }
  )
}
</script>

<template>
  <div class="mt-5 mb-10">
    <h3 class="font-bold text-xl">Skills</h3>
    <p class="mt-1 mb-5 text-sm text-gray-400">Choose 5 of the most important skills to show your talents! Make sure they
      match the keyword of the job listing if applying via an online system</p>
      <div class="mb-8" v-show="isForm">
        <input
          class="mr-2 mt-[0.3rem] h-3.5 w-8 appearance-none rounded-[0.4375rem] bg-neutral-300 before:pointer-events-none before:absolute before:h-3.5 before:w-3.5 before:rounded-full before:bg-transparent before:content-[''] after:absolute after:z-[2] after:-mt-[0.1875rem] after:h-5 after:w-5 after:rounded-full after:border-none after:bg-neutral-100 after:shadow-[0_0px_3px_0_rgb(0_0_0_/_7%),_0_2px_2px_0_rgb(0_0_0_/_4%)] after:transition-[background-color_0.2s,transform_0.2s] after:content-[''] checked:bg-primary checked:after:absolute checked:after:z-[2] checked:after:-mt-[3px] checked:after:ml-[1.0625rem] checked:after:h-5 checked:after:w-5 checked:after:rounded-full checked:after:border-none checked:after:bg-primary checked:after:shadow-[0_3px_1px_-2px_rgba(0,0,0,0.2),_0_2px_2px_0_rgba(0,0,0,0.14),_0_1px_5px_0_rgba(0,0,0,0.12)] checked:after:transition-[background-color_0.2s,transform_0.2s] checked:after:content-[''] hover:cursor-pointer focus:outline-none focus:ring-0 focus:before:scale-100 focus:before:opacity-[0.12] focus:before:shadow-[3px_-1px_0px_13px_rgba(0,0,0,0.6)] focus:before:transition-[box-shadow_0.2s,transform_0.2s] focus:after:absolute focus:after:z-[1] focus:after:block focus:after:h-5 focus:after:w-5 focus:after:rounded-full focus:after:content-[''] checked:focus:border-primary checked:focus:bg-primary checked:focus:before:ml-[1.0625rem] checked:focus:before:scale-100 checked:focus:before:shadow-[3px_-1px_0px_13px_#3b71ca] checked:focus:before:transition-[box-shadow_0.2s,transform_0.2s] dark:bg-neutral-600 dark:after:bg-neutral-400 dark:checked:bg-primary dark:checked:after:bg-primary dark:focus:before:shadow-[3px_-1px_0px_13px_rgba(255,255,255,0.4)] dark:checked:focus:before:shadow-[3px_-1px_0px_13px_#3b71ca]"
          type="checkbox"
          role="switch"
          id="flexSwitchCheckDefault" />
        <label
          class="inline-block pl-[0.65rem] hover:cursor-pointer"
          for="flexSwitchCheckDefault"
          >Don't show experience level</label
        >
      </div>
      
    <div class="flex flex-row flex-wrap">
      <Checkbox :label="label" v-for="(label, index) in checkBoxLabel" :key="index" />
    </div>
    <div class="mt-2 mb-5">
      <button class="text-blue-400 font-semibold text-sm" @click="showForm" v-if="!isForm">+ Add skill</button>
      <div class="border rounded-sm py-4 px-6 mb-4" v-else v-for="(skill, indexSkill) in skills" :key="indexSkill">
        <div class="flex flex-row justify-between mb-4">
          <div class="flex flex-col">
            <p class="font-semibold mt-3">{{ skill.skill ? skill.skill : '(not specified) ' }}</p>
            <p class="text-gray-400 text-[15px]" v-show="skill.picked">{{ skill.picked}}</p>
          </div>

          <button class="p-3" @click="toogleForm(indexSkill)">
            <svg fill="#000000" width="30px" height="30px"
              :class="{ 'rotate-180 transition-all ease-out duration-200': skill.toggle }" viewBox="-5 -7.5 24 24"
              xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMinYMin" class="jam jam-chevron-up">
              <path
                d='M7.071 2.828l-4.95 4.95A1 1 0 0 1 .707 6.364L6.364.707a1 1 0 0 1 1.414 0l5.657 5.657a1 1 0 0 1-1.414 1.414l-4.95-4.95z' />
            </svg>
          </button>
        </div>
        <div v-if="!skill.toggle">
          <div class="flex flex-row justify-start">
            <Input :label="'Skill'" :wInput="'w-full'" class="w-[48%] mr-8" v-model="skill.skill" />
            <div class="w-1/2">
              <label class="text-gray-400 text-xs mb-2" :for="skill.value">Level - <span class="font-semibold"
                  :class="{ 'text-blue-700': skill.picked === 'Expert', 'text-green-700': skill.picked === 'Experienced', 'text-blue-400': skill.picked === 'Basic', 'text-green-400': skill.picked === 'Medium', 'text-lime-500': skill.picked === 'Skillful', }">{{
                    skill.picked }}</span></label>
              <div class="flex flex-row">
                <label class="cursor-pointer w-full justify-start my-2 border-l-2 first:border-none" :class="{ 'border-blue-600': skill.picked === 'Expert', 'border-green-600': skill.picked === 'Experienced', 'border-blue-300': skill.picked === 'Basic', ' border-green-300': skill.picked === 'Medium', 'border-lime-400': skill.picked === 'Skillful', }" v-for="(exp, expIndex) in skillExp" :key="expIndex"
                  :for="`${indexSkill}_`+exp.value">
                  <input type="radio" :id="`${indexSkill}_`+exp.value" :value="exp.value" v-model="skill.picked" class="hidden peer" />
                  <p class="rounded-sm p-5 "
                    :class="{ 'peer-checked:bg-blue-600 bg-blue-200 border-blue-600': skill.picked === 'Expert', 'peer-checked:bg-green-600 bg-green-200 border-green-600': skill.picked === 'Experienced', 'peer-checked:bg-blue-300 bg-blue-50 border-blue-300': skill.picked === 'Basic', 'peer-checked:bg-green-300 bg-green-100 border-green-300': skill.picked === 'Medium', 'peer-checked:bg-lime-400 bg-lime-100 border-lime-400': skill.picked === 'Skillful', }">
                  </p>
                </label>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <button class="text-blue-400 font-semibold text-sm" v-if="isForm" @click="addRow">+ Add One More Skill</button>
  </div>
</template>

<style scoped>

</style>