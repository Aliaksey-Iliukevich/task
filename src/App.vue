<template>
  <div>
    <SearchInput label="Input value:" v-model="value" :font-size="fontSize" :input-classes="inputClasses" @update:value="UpdateInputValue" @clearInput="handleClearInput" />
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
      value: '', // реактивное изм. значения введённого в поле поиска
      fontSize: 20, // установить нужный размер шрифта
      inputClasses: 'class-1, class-2' // классы передаваемые в инпут
    };
  },
  methods: {
    UpdateInputValue(newValue) {
      this.value = newValue;
    },
    handleClearInput() {
      console.log('Инпут очищен!');
    }
  }
};
</script>