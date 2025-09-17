<template>
  <div class="fastfetch-container">
    <pre v-html="displayedText"></pre>
    <span class="cursor">|</span>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const lines = [
  `<span class="user">Jelly@Jellys-Site.local</span>`,
  "--------------------------",
  `<span class="label">OS:</span> FrogOS :: unstable build 0.01.14`,
  `<span class="label">Kelnel:</span> custom-ribbit-kelnel v4rog`,
  `<span class="label">Shell:</span> Bash`,
  `<span class="label">Runtime:</span> Python + JavaScript`,
  `<span class="label">Mood:</span> Mlem Mlem`,
  `<span class="label">Projects:</span> 42`,
  `<span class="label">Fun Fact:</span> All hat, no cattle`,
  `<span class="label">Status:</span> Sleeping...`
]

const displayedText = ref("")

onMounted(() => {
  let lineIndex = 0

  function typeLine(line, i = 0) {
    if (i < line.length) {
      displayedText.value += line[i]
      setTimeout(() => typeLine(line, i + 1), 25)
    } else {
      displayedText.value += "\n"
      lineIndex++
      if (lineIndex < lines.length) {
        setTimeout(() => typeLine(lines[lineIndex]), 150)
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

.user {
  color: var(--vt-c-accent-bright);
}
.label {
  color: var(--vt-c-accent-blue);
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
