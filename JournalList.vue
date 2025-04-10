<template>
  <div class="journal-list">
    <div v-for="(entry, index) in entries" :key="index" class="entry">
      <div class="date">{{ entry.date }}</div>
      <div v-html="renderMarkdown(entry.content)" class="content" />
    </div>
  </div>
</template>

<script>
import { marked } from 'marked'
import hljs from 'highlight.js'

marked.setOptions({
  highlight: (code, lang) => {
    return hljs.highlightAuto(code, [lang]).value
  }
})

export default {
  props: ['entries'],
  methods: {
    renderMarkdown(text) {
      return marked(text)
    }
  }
}
</script>

<style scoped>
.journal-list .entry {
  border-bottom: 1px solid #444;
  padding: 1rem 0;
}
.journal-list .date {
  font-size: 0.9rem;
  color: #bbb;
}
.journal-list .content :deep(pre) {
  background-color: #2d2d2d;
  padding: 1rem;
  overflow: auto;
  border-radius: 5px;
}
</style>
