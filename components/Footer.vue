<script setup>
const props = defineProps({
  blurb: String,
  columns: Array,
  legal: String,
  company: Object,
});
</script>

<template>
  <footer class="border-t border-white/6 bg-ink-950">
    <Container>
      <div class="grid gap-12 py-16 lg:grid-cols-[22rem_1fr] lg:gap-20">
        <div>
          <Wordmark size="lg" />
          <p v-if="blurb" class="max-w-sm mt-5 text-sm leading-relaxed text-mist-400">{{ blurb }}</p>
        </div>

        <div class="grid gap-10 sm:grid-cols-3">
          <div v-for="column of columns" :key="column.title">
            <p class="eyebrow text-mist-500">{{ column.title }}</p>
            <ul class="mt-4 space-y-2.5">
              <li v-for="link of column.links" :key="link.label">
                <NuxtLink
                  :href="link.url"
                  class="text-sm transition-colors duration-200 text-mist-300 hover:text-brass-300"
                >
                  {{ link.label }}
                </NuxtLink>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <div class="flex flex-col gap-3 py-6 border-t border-white/6 sm:flex-row sm:items-center sm:justify-between">
        <p class="font-mono text-2xs tracking-wide text-mist-500">
          &copy; {{ new Date().getFullYear() }} {{ company?.name || "Ezana AI" }}. All rights reserved.
        </p>
        <p v-if="legal" class="font-mono text-2xs tracking-wide text-mist-500">{{ legal }}</p>
      </div>
    </Container>
  </footer>
</template>
