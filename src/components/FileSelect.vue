<template>
  <label class="file-select">
    <div class="select-button">
      <span v-if="file">Selected File: {{file.name}}</span>
      <span v-else>Select File</span>
    </div>
    <input type="file" @change="handleFileChange"/>
  </label>
</template>

<script lang="ts">
export default {
  data: function () {
    return {
      file: null
    }
  },
  methods: {
    /**
     * When a file is uploaded, this event fires.
     * Emits the File object to the parent
     * @param e File Event
     */
    handleFileChange (e: any) {
      let newfile = e.target.files[0]
      this.$emit('new-file', newfile)
      this.file = newfile
    }
  }
}
</script>

<style scoped>
.file-select > .select-button {
  padding: 1rem;

  color: white;
  background-color: #2EA169;

  border-radius: .3rem;

  text-align: center;
  font-weight: bold;
}

.file-select > input[type="file"] {
  display: none;
}
</style>
