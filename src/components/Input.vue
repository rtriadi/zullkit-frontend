<script setup>
defineProps({
  label: String,
  placeholder: String,
  id: String,
  type: {
    type: String,
    default: "text",
  },
  name: String,
  inputClass: {
    type: String,
    default:
      "block w-full py-3 mt-2 border border-gray-300 rounded-full shadow-sm px-7 focus:border-indigo-300 focus:outline-none focus:ring focus:ring-indigo-200 focus:ring-opacity-50 disabled:bg-gray-100",
  },
  modelValue: [String, Number],
});
defineEmits(["update:modelValue"]);
</script>
<template>
  <div class="mb-4">
    <Label class="block mb-1" :for="id">{{ label }}</Label>
    <input
      :placeholder="placeholder"
      :id="id"
      :type="type"
      :name="name"
      :class="inputClass"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>
