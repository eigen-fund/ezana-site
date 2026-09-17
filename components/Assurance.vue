<script setup>
defineProps({
  eyebrow: String,
  title: String,
  description: String,
  columns: Array,
});
</script>

<template>
  <section id="assurance" class="py-24 border-t border-white/6 bg-ink-900/40 sm:py-32 scroll-mt-16">
    <Container>
      <SectionHeading :eyebrow="eyebrow" :title="title" :description="description" />

      <div class="grid gap-x-10 gap-y-12 mt-16 sm:grid-cols-2 lg:grid-cols-4">
        <div v-for="column of columns" :key="column.title">
          <h3 class="pb-4 text-sm font-medium border-b text-mist-100 border-brass-400/30">
            {{ column.title }}
          </h3>
          <ul class="mt-5 space-y-3">
            <li
              v-for="line of column.items"
              :key="line"
              class="text-sm leading-relaxed text-mist-400"
            >
              {{ line }}
            </li>
          </ul>
        </div>
      </div>
    </Container>
  </section>
</template>
