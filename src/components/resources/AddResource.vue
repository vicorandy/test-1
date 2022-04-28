<template>
  <base-dialog v-if="inputIsValid" title="Invalid Input" @close="confirmError">
    <template v-slot:default>
      <p>At leats one input is invalid</p>
      <p>
        check all inputs and make sure that enter at least a few chararcters
        into each input field
      </p>
    </template>
    <template v-slot:actions>
      <base-button v-on:click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form v-on:submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          type="text"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="linkInput" />
      </div>
      <base-button>Add Resource</base-button>
    </form>
  </base-card>
</template>
<script>
export default {
  inject: ['update'],
  data() {
    return {
      inputIsValid: false,
    };
  },
  methods: {
    submitData() {
      const newResource = {};
      newResource.id = new Date().toISOString;
      newResource.title = this.$refs.titleInput.value;
      newResource.description = this.$refs.descInput.value;
      newResource.link = this.$refs.linkInput.value;
      if (
        newResource.title.trim() === '' ||
        newResource.description.trim() === '' ||
        newResource.link.trim() === ''
      ) {
        this.inputIsValid = true;
        return;
      }
      this.update(newResource);
      // this.$emit('update', newResource);
    },
    confirmError() {
      this.inputIsValid = false;
    },
  },
};
</script>
<style scoped>
label {
  font-weight: bold;
  display: block;
  margin: bottom 0.5rem;
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
