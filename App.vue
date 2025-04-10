<template>
  <div class="app">
    <h1>Dev Journal</h1>
    <JournalEditor @save="saveEntry" />
    <JournalList :entries="entries" />
  </div>
</template>

<script>
import JournalEditor from './components/JournalEditor.vue'
import JournalList from './components/JournalList.vue'

export default {
  components: {
    JournalEditor,
    JournalList
  },
  data() {
    return {
      entries: []
    }
  },
  methods: {
    saveEntry(entry) {
      this.entries.unshift(entry)
      localStorage.setItem('dev-journal', JSON.stringify(this.entries))
    }
  },
  mounted() {
    const saved = localStorage.getItem('dev-journal')
    if (saved) this.entries = JSON.parse(saved)
  }
}
</script>

<style scoped>
.app {
  padding: 20px;
  font-family: Arial, sans-serif;
  color: #fff;
  background-color: #333;
}
h1 {
  color: #ff6347;
}
</style>
