<template>
  <base-dialog v-if="inputIsInvalid" @close="closeDialog" title="Invalid Input">
    <template #default>
      <p>Unfortunately, at least one input is invalid</p>
      <p>Make sure you entered at least few characters for each input</p>
    </template>
    <template #actions>
      <base-button @click="closeDialog"> Okay </base-button>
    </template>
  </base-dialog>
  <base-card>
    <h2>Add Resource</h2>
    <form @submit.prevent="submitForm">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="titleInput" />
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
        <input type="url" name="link" id="link" ref="linkInput" />
      </div>
      <base-button type="submit">Add Resource</base-button>
    </form>
  </base-card>
</template>

<script>
import BaseDialog from "../../UI/BaseDialog.vue";
export default {
  components: { BaseDialog },
  inject: ["addResource"],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    submitForm() {
      const titleInput = this.$refs.titleInput.value.trim();
      const descInput = this.$refs.descInput.value.trim();
      const urlInput = this.$refs.linkInput.value.trim();
      if (titleInput === "" || descInput === "" || urlInput === "") {
        this.inputIsInvalid = true;
      } else {
        this.addResource(titleInput, descInput, urlInput);
      }
    },
    closeDialog() {
      this.inputIsInvalid = false;
    },
  },
};
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