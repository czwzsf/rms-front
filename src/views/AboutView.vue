<template>
  <div>
    <select v-model="selectedValue1">
      <option v-for="option in options1" v-bind:key="option.id" :value="option.value">
        {{ option.text }}
      </option>
    </select>
    <select v-model="selectedValue2" :disabled="!selectedValue1">
      <option v-for="option in options2[selectedValue1]" v-bind:key="option.id" :value="option.value">
        {{option.text }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedValue1: null,
      selectedValue2: null,
      options1: [
        {value: 1, text: 'Option 1'},
        {value: 2, text: 'Option 2'},
        {value: 3, text: 'Option 3'}
      ],
      options2: {
        1: [
          {value: 'a', text: 'Option 1-1'},
          {value: 'b', text: 'Option 1-2'},
          {value: 'c', text: 'Option 1-3'}
        ],
        2: [
          {value: 'd', text: 'Option 2-1'},
          {value: 'e', text: 'Option 2-2'},
          {value: 'f', text: 'Option 2-3'}
        ],
        3: [
          {value: 'g', text: 'Option 3-1'},
          {value: 'h', text: 'Option 3-2'},
          {value: 'i', text: 'Option 3-3'}
        ]
      }
    }
  }
}
</script>
