<template>
  <form @submit="onSubmit">
    <div class="w-100 mx-auto position-relative mb-5">
      <input
        class="form-control mx-auto bg-secondary"
        type="text"
        placeholder="Enter a movie
    name"
        v-model="key"
      />
      <i
        @click="$emit('search-click')"
        class="bg-secondary text-dark fa-solid fa-magnifying-glass position-absolute top-50 end-0 translate-middle-y me-3"
      ></i>
    </div>
  </form>
</template>

<script>
export default {
  name: 'Search',
  data() {
    return {
      key: '',
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.key) {
        alert('Please enter a movie name');
        return;
      }

      const newSearch = {
        key: this.key,
      };
      this.$emit('make-search', newSearch);
      console.log(this.key);
      this.key = ''; // to clear the form
    },
  }, //    this.$emit('search-click');
};
</script>

<style scope>
i {
  cursor: pointer;
}
</style>
