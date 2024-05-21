<template>
  <div>
    <SearchInput label="Input value:" v-model="modelValue" :font-size="fontSize" :input-classes="inputClasses.join(' ')" @update:value="updateInputValue" @clearInput="handleClearInput" />
  </div>
</template>

<script>
import SearchInput from './components/SearchInput.vue';

export default {
  components: {
    SearchInput
  },
  data() {
    return {
      modelValue: '', // Реактивное изменение значения введенного в поле поиска
      fontSize: 20, // Установлен нужный размер шрифта
      inputClasses: ['class-1', 'class-2'] // Классы, передаваемые в инпут
    };
  },
  methods: {
    updateInputValue(newValue) {
      this.modelValue = newValue;
    },
    handleClearInput() {
      this.modelValue = '';
      console.log('Инпут очищен!');
    }
  }
};
</script>