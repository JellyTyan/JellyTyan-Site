<template>
  <div class="fastfetch-container">
    <pre>{{ displayedText }}</pre>
    <span class="cursor">|</span>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const lines = [
  "Jelly@Jellys-Site.local",
  "--------------------------",
  "OS: FrogOS :: stable build 1.00.12",
  "Kelnel: custom-ribbit-kelnel v4rog",
  "Shell: Bash",
  "Runtime: Python + JavaScript + Java",
  "Mood: Mlem Mlem",
  "Projects: 5",
  "Fun Fact: All hat, no cattle",
  "Status: Sleeping..."
]

const displayedText = ref("")

onMounted(() => {
  let lineIndex = 0

  function typeLine(line, i = 0) {
    if (i < line.length) {
      displayedText.value += line[i]
      setTimeout(() => typeLine(line, i + 1), 50)
    } else {
      displayedText.value += "\n"
      lineIndex++
      if (lineIndex < lines.length) {
        setTimeout(() => typeLine(lines[lineIndex]), 200)
      }
    }
  }

  typeLine(lines[0])
})
</script>

<style scoped>
.fastfetch-container {
  font-family: 'Fira Code', monospace;
  color: var(--vt-c-text-light-1);
  white-space: pre;
  font-size: 16px;
  line-height: 1.4;
}

.cursor {
  display: inline-block;
  width: 1ch;
  animation: blink 1s steps(2, start) infinite;
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}
</style>
