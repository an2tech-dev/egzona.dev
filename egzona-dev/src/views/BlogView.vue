<template>
    <div class="blog" v-html="content"></div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue'
  import MarkdownIt from 'markdown-it'
  
  const md = new MarkdownIt()
  const content = ref('')
  
  onMounted(async () => {
    const post = await import('../content/hello.md?raw')
    content.value = md.render(post.default)
  })
  </script>