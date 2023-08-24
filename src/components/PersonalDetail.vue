<script setup>
import { ref } from 'vue';
import Input from './ui/Input.vue'


const currentImage = ref(undefined)
const previewImage = ref(undefined)
const file = ref(null)

const selectImage = () => {
  currentImage.value = file.value.files[0];
  previewImage.value = URL.createObjectURL(currentImage.value);
}
</script>

<template>
  <div>
    <h3 class="font-bold text-xl">Personal Details</h3>
    <div class="flex flex-row w-full justify-start mt-3">
      <Input :label="'Wanted Job Title'" :is-info="true" class="mr-10"/>
      <div>
        <label for="upload-image" class="border-[#0F96CD] text-[#0F96CD] flex flex-row rounded w-full py-2 mt-4 justify-start cursor-pointer">
          <input
            id="upload-image"
            type="file"
            accept="image/png, image/jpg, image/jpeg"
            ref="file"
            @change="selectImage"
            class="hidden"
          />
            <div class="bg-gray-100 p-2 rounded " v-if="!currentImage">
            <svg width="35px" height="35px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M15 8.5C15 10.433 13.433 12 11.5 12C9.567 12 8 10.433 8 8.5C8 6.567 9.567 5 11.5 5C13.433 5 15 6.567 15 8.5Z"
                fill="grey" />
              <path
                d="M17.6305 20H5.94623C5.54449 20 5.31716 19.559 5.56788 19.2451C6.68379 17.8479 9.29072 15 12 15C14.7275 15 17.0627 17.8864 18.0272 19.2731C18.2474 19.5897 18.0161 20 17.6305 20Z"
                fill="grey" stroke="grey" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
            </svg>
          </div>
          <img class="w-16 h-16 rounded" :src="previewImage" alt=""  v-else />
          <p class="text-sm pl-4 pt-4">Upload Foto</p>
        </label>
      </div>
    </div> 
    <div class="flex flex-row w-full justify-start">
      <Input :label="'First Name'" class="mr-10"/>
      <Input :label="'Last Name'" />
    </div>
    <div class="flex flex-row w-full justify-start">
      <Input :label="'Email'" class="mr-10"/>
      <Input :label="'Phone'" />
    </div>
    <div class="flex flex-row w-full justify-start">
      <Input :label="'Country'" class="mr-10"/>
      <Input :label="'City'" />
    </div>
    <div class="flex flex-row w-full justify-start">
      <Input :label="'Address'" class="mr-10"/>
      <Input :label="'Postal Code'" />
    </div>
    <div class="flex flex-row w-full justify-start">
      <Input :label="'Driving License'" :is-info="true" class="mr-10"/>
      <Input :label="'Nationality'" />
    </div>
    <div class="flex flex-row w-full justify-start">
      <Input :label="'Place of Birth'" :is-info="true" class="mr-10"/>
      <Input :label="'Date of Birth'" :is-info="true"/>
    </div>
  </div>
</template>

