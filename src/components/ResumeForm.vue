<template>
    <form class="card card-w30" @submit.prevent="submitForm">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="type">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea id="value" v-model="value" rows="3"></textarea>
      </div>

      <button class="btn primary" type="submit" :disabled="!isValid">Добавить</button>
    </form>
</template>

<script>
export default {
  emits: ['add-block'],
  data () {
    return {
      type: 'title',
      value: ''
    }
  },
  computed: {
    isValid () {
      return this.value.length > 3
    }
  },
  methods: {
    submitForm () {
      this.$emit('add-block', {
        type: this.type,
        value: this.value,
        id: Date.now()
      })
      this.type = 'title'
      this.value = ''
    }
  }
}
</script>

<style>

</style>
