<script setup>
defineProps({
  eyebrow: String,
  title: String,
  description: String,
  steps: Array,
});
</script>

<template>
  <section id="how-it-runs" class="py-24 border-t border-white/6 bg-ink-900/40 sm:py-32 scroll-mt-16">
    <Container>
      <SectionHeading :eyebrow="eyebrow" :title="title" :description="description" />

      <ol class="mt-16 lg:flex lg:gap-px">
        <li
          v-for="(step, i) of steps"
          :key="step.index"
          class="relative flex-1 py-8 pl-8 border-l lg:py-0 lg:pl-0 lg:pt-10 lg:border-l-0 lg:border-t border-white/10"
        >
          <!-- node on the rail -->
          <span
            class="absolute w-2 h-2 rounded-full -left-1 top-9 lg:left-0 lg:-top-1"
            :class="i === 0 ? 'bg-brass-400' : 'bg-ink-600'"
            aria-hidden="true"
          />
          <div class="lg:pr-8">
            <p class="font-mono text-2xs tracking-widest text-brass-500">{{ step.index }}</p>
            <h3 class="mt-3 text-base font-medium text-mist-100">{{ step.title }}</h3>
            <p class="mt-2.5 max-w-sm text-sm leading-relaxed text-mist-400">{{ step.description }}</p>
          </div>
        </li>
      </ol>
    </Container>
  </section>
</template>
