<template>
  <div class="journal-editor">
    <textarea v-model="content" placeholder="Write your thoughts or code here..." />
    <button @click="submitEntry">Save Entry</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      content: ''
    }
  },
  methods: {
    submitEntry() {
      if (!this.content.trim()) return
      this.$emit('save', {
        content: this.content,
        date: new Date().toLocaleString()
      })
      this.content = ''
    }
  }
}
</script>

<style scoped>
.journal-editor textarea {
  width: 100%;
  height: 150px;
  padding: 10px;
  font-family: monospace;
  margin-bottom: 10px;
}
.journal-editor button {
  background-color: #3b82f6;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
}
</style>
