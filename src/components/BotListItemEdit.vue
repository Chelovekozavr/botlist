<template>
  <div class="add-bot">

    <div class="add-bot__header">
      <h3 class="add-bot__title">
        Edit bot
      </h3>
      <button
        class="add-bot__close-button"
        @click="$emit('cancel-edit')"
      >
        X
      </button>
    </div>

    <form
      action=""
      method="POST"
      class="add-bot__form"
      @submit.prevent="$emit('submit-editing', botToEdit)"
    >
      <input
        type="text"
        class="add-bot__form-item"
        v-model="botToEdit.name"
        required
      >
      <input
        type="text"
        maxlength="50"
        class="add-bot__form-item"
        v-model.trim="botToEdit.description"
        required
      >
      <input
        type="date"
        class="add-bot__form-item"
        v-model="botToEdit.date"
        required
      >
      <input
        type="file"
        class="add-bot__form-item add-bot__form-image"
        id="image"
        value="image"
        @change="editImage"
      >
      <label for="image" class="add-bot__form-item add-bot__label">
        {{ botToEdit.image ? botToEdit.image : "Drag image here"}}
      </label>

      <button
        class="add-bot__submit-button"
      >
        Submit
      </button>
    </form>

  </div>
</template>

<script>
  export default {
    props: {
      bot: Object
    },

    data() {
      return {
        botToEdit: { ...this.bot }
      }
    },

    methods: {
      editImage() {
        let imagePath = document.getElementById("image").value;
        let imageName = imagePath.split('\\');
        this.botToEdit.image = imageName[imageName.length - 1];
      }
    }
  }
</script>

<style lang="scss" scoped>
  .add-bot {
    position: absolute;
    top: 50px;
    padding: 30px;

    width: calc(60% - 60px);
    max-width: 940px;

    background-color: #76787a;
    box-shadow: 0 5px 1000px 1000px rgba(0,0,0, 0.75);

    &__header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;

      text-transform: uppercase;
      font-weight: bold;
      position: relative;
      color: #6Ba2e0;

      &::after {
        content: '';
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 3px;
        background-color: whitesmoke;
        z-index: 10;
      }
    }

    &__title {
      position: relative;
      font-size: 20px;

      &::after {
        content: '';
        position: absolute;

        bottom: 0;
        width: 100%;
        height: 3px;
        color: whitesmoke;
      }
    }

    &__close-button {
      height: 40px;
      width: 40px;
      border-radius: 50%;

      background-color: #76787a;
      color: #fff;
      border: none;
      outline: none;

      font-weight: bold;
      font-size: 20px;
      transition: background-color 0.5s ease,
        transform 0.5s ease;

      &:hover {
        background-color: #6a6c6e;
      }

      &:active {
        transform: scale(0.9);
      }
    }

    &__form {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      position: relative;
    }

    &__form-item {
      height: 40px;
      width: 45%;
      margin-bottom: 10px;

      font-size: 18px;
      color: #76787a;
    }

     &__form-image {
      opacity: 0;
      z-index: 1;
      cursor: pointer;
    }

    &__label {
      width: 45%;
      display: flex;
      align-items: center;


      position: absolute;
      bottom: 50px;
      right: 0;
      padding: 2px;
      height: 40px;

      font-size: 18px;
      color: #76787a;
      background-color: #fff;
      border: 2px dashed #979a9c;
      outline: 1px;

      cursor: pointer;
    }

    &__submit-button {
      height: 50px;
      width: 200px;
      margin: 0 auto 0;

      background-color: #5d5f61;
      color: #fff;
      border: none;

      text-transform: uppercase;
      font-weight: bold;
      font-size: 18px;
      letter-spacing: .1rem;

      transition: background-color 0.5s ease,
        transform 0.5s ease;

      &:hover {
        background-color: #979a9c;
      }

      &:active {
        transform: scale(0.9);
      }
    }
  }
</style>
