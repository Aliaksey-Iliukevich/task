<template>
  <div>
    <SearchInput 
      label="Input value:" 
      v-model="search"
      class="class-1 class-2"
      :font-size="fontSize"
      placeholder="Найти..."
      @clearInput="handleClearInput"
    />
    {{ search }}
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
      search: '', // Реактивное изменение значения введенного в поле поиска
      fontSize: 20, // Установлен нужный размер шрифта
      inputClasses: ['class-1', 'class-2'] // Классы, передаваемые в инпут
    };
  },
  methods: {
    handleClearInput() {
      console.log('Инпут очищен!');
    }
  }
};
</script>