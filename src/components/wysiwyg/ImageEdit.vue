<template>
  <div class="image-edit">
    <input
        ref="file"
        type="file"
        @change="onFileSelect"
        hidden
    >
    <div
        v-if="url"
        class="image-edit__control-panel">
      <div
          class="image-edit__control-panel__delete"
          @click="removeImage"
      >
        DEL
      </div>
    </div>
    <img
        v-if="!url"
        src="https://via.placeholder.com/360x240"
        alt="placeholder image"
        class="image-edit__image"
        @click="changeImage"
    >
    <img
        v-else
        :src="url"
        alt="placeholder image"
        class="image-edit__image"
        @click="changeImage"
    >
  </div>
</template>

<script>
export default {
  name: 'ImageEdit',
  data() {
    return {
      selectedFile: null,
      url: null,
    }
  },
  methods: {
    onFileSelect(event) {
      const file = event.target.files[0]
      this.url = URL.createObjectURL(file);
      this.selectedFile = file;
    },
    changeImage() {
      this.$refs.file.click();
    },
    removeImage() {
      this.url = null;
      this.selectedFile = null;
    }
  }
}
</script>

<style lang="less">
.image-edit {
  position: relative;
  width: 100%;

  border: 3px solid transparent;

  &:hover {
    border: 3px solid #42b983;
  }
}

.image-edit__image {
  width: 100%;
}

.image-edit__control-panel {
  position: absolute;
  right: 0;
  top: 0;

  padding: 2px 8px;

  background-color: #42b983;
  color: white;
}

.image-edit__control-panel__delete {
  cursor: pointer;
}
</style>