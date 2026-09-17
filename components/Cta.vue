<script setup>
defineProps({
  eyebrow: String,
  title: String,
  description: String,
  buttons: Array,
});
</script>

<template>
  <section class="py-24 border-t border-white/6 sm:py-32">
    <Container>
      <div class="relative overflow-hidden border rounded-2xl border-white/10 bg-ink-900/70">
        <div class="absolute inset-0 grid-field opacity-40" aria-hidden="true" />
        <div
          class="absolute inset-0"
          style="background: radial-gradient(60% 80% at 15% 0%, rgba(211,173,98,0.14), transparent 70%)"
          aria-hidden="true"
        />
        <span class="absolute inset-x-0 top-0 h-px bg-linear-to-r from-transparent via-brass-400/50 to-transparent" aria-hidden="true" />

        <div class="relative px-8 py-14 sm:px-14 sm:py-16 lg:px-16 lg:py-20">
          <p v-if="eyebrow" class="eyebrow text-brass-400">{{ eyebrow }}</p>
          <h2 v-if="title" class="max-w-2xl mt-5 text-3xl font-medium tracking-tight text-balance text-mist-100 sm:text-4xl">
            {{ title }}
          </h2>
          <p v-if="description" class="max-w-2xl mt-5 text-base leading-relaxed text-mist-400 sm:text-lg">
            {{ description }}
          </p>
          <div class="flex flex-wrap gap-3 mt-9">
            <ActionLink
              v-for="button of buttons"
              :key="button.label"
              :label="button.label"
              :url="button.url"
              :variant="button.variant"
            />
          </div>
        </div>
      </div>
    </Container>
  </section>
</template>
