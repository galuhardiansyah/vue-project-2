<script setup>
import { computed } from 'vue';

const props = defineProps(
  {
    isInfo: {
      type:Boolean, 
      default:false 
    },
    label:{
      type:String,
    },
    modelValue:{},
    type:{
      type:String,
      default:'text'
    },
    wInput:{
      type:String,
      default: 'w-[520px]'
    },
    maxDate:{
      type:Number,
      default: null
    }
  }
)
const emit = defineEmits(['update:modelValue'])
const value = computed({
  get(){
    return props.modelValue
  },
  set(value){
    emit('update:modelValue', value)
  }
})

</script>

<template>
  <div class="flex flex-col my-2">
    <label :for="'id' + props.label" v-if="props.label" class="text-gray-400 text-xs mb-2 flex flex-row">
      {{ props.label }}
      <svg v-show="props.isInfo" width="16px" height="16px" class="ml-1" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path d="M11 12H9v-.148c0-.876.306-1.499 1-1.852.385-.195 1-.568 1-1a1.001 1.001 0 00-2 0H7c0-1.654 1.346-3 3-3s3 1 3 3-2 2.165-2 3zm-2 3h2v-2H9v2z" fill="#5d6ee5"/><path d="M10 4a6 6 0 100 12 6 6 0 000-12zm-8 6a8 8 0 1116 0 8 8 0 01-16 0z" fill="#5d6ee5" /></svg>
    </label>
    <input :id="'id' + props.label" :type="props.type" v-model="value" :max="new Date(maxDate).toISOString().split('T')[0]" class="bg-blue-50 rounded-sm py-2 px-2 focus:outline-none focus:border-b-2 focus:border-blue-500" :class="wInput">
  </div>
  
</template>