<template>
  <base-dialog
    v-if="isInvalidInput"
    title="Invalid Input"
    @closeDialog="closeDialog"
  >
    <template #default>
      <p>Unfortunately input is invalid!</p>
      <p>mk sure u entered correct inputs!</p>
    </template>

    <template #actions>
      <base-button @click="closeDialog">okay </base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title:</label>
        <input
          type="text"
          id="title"
          name="title"
          placeholder="write the title"
          ref="titleInput"
        />
      </div>
      <div class="form-control">
        <label for="desc">Description:</label>
        <textarea
          id="desc"
          name="desc"
          placeholder="write the description"
          rows="2"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link:</label>
        <input
          type="url"
          id="link"
          name="link"
          placeholder="write the link"
          ref="linkInput"
        />
      </div>

      <base-button type="submit">Add Resource</base-button>
    </form>
  </base-card>
</template>

<script>
import BaseButton from "../UI/BaseButton.vue";
import BaseCard from "../UI/BaseCard.vue";
export default {
  components: { BaseCard, BaseButton },
  name: "AddResource",
  inject: ["addResource"],
  data() {
    return {
      isInvalidInput: false,
    };
  },

  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDesc = this.$refs.descInput.value;
      const enteredLink = this.$refs.linkInput.value;
      if (
        enteredLink.trim() === "" ||
        enteredDesc.trim() === "" ||
        enteredTitle.trim() === ""
      ) {
        this.isInvalidInput = true;
        return;
      }
      this.addResource(enteredTitle, enteredDesc, enteredLink);
    },
    closeDialog() {
      this.isInvalidInput = false;
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
