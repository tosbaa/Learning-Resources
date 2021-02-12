<template>
  <base-card>
    <h2>Add Resource</h2>
    <form @submit.prevent="submitForm">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="titleInput"/>
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          name="description"
          id="description"
          cols="30"
          rows="10"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" name="link" id="link" ref="linkInput"/>
      </div>
      <base-button type="submit">Add Resource</base-button>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['addResource'],
  methods: {
    submitForm() {
      const titleInput = this.$refs.titleInput.value;
      const descInput = this.$refs.descInput.value;
      const urlInput = this.$refs.linkInput.value;
      this.addResource(titleInput, descInput, urlInput);
    },
  }
}
</script>



<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>