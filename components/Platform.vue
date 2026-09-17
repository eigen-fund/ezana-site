<script setup>
defineProps({
  eyebrow: String,
  title: String,
  description: String,
  items: Array,
});
</script>

<template>
  <section id="platform" class="py-24 sm:py-32 scroll-mt-16">
    <Container>
      <SectionHeading :eyebrow="eyebrow" :title="title" :description="description" />

      <div class="grid mt-16 border-t border-l border-white/6 sm:grid-cols-2 lg:grid-cols-3">
        <div
          v-for="item of items"
          :key="item.title"
          class="relative p-8 border-b border-r group border-white/6 transition-colors duration-300 hover:bg-ink-900/60"
        >
          <span
            class="absolute inset-x-0 top-0 h-px transition-opacity duration-300 opacity-0 bg-linear-to-r from-transparent via-brass-400/50 to-transparent group-hover:opacity-100"
            aria-hidden="true"
          />
          <Glyph :name="item.glyph" :size="22" class="text-brass-400" />
          <h3 class="mt-5 text-base font-medium text-mist-100">{{ item.title }}</h3>
          <p class="mt-3 text-sm leading-relaxed text-mist-400">{{ item.description }}</p>
        </div>
      </div>
    </Container>
  </section>
</template>
