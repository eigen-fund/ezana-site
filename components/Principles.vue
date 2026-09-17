<script setup>
defineProps({
  eyebrow: String,
  title: String,
  items: Array,
});
</script>

<template>
  <section class="py-20 border-y border-white/6 bg-ink-900/40 sm:py-24">
    <Container>
      <div class="grid gap-14 lg:grid-cols-[22rem_1fr] lg:gap-16">
        <div>
          <p v-if="eyebrow" class="eyebrow text-brass-400">{{ eyebrow }}</p>
          <h2 v-if="title" class="mt-5 text-2xl font-medium tracking-tight text-balance text-mist-100 sm:text-3xl">
            {{ title }}
          </h2>
        </div>

        <dl class="grid gap-x-12 gap-y-10 sm:grid-cols-2">
          <div v-for="item of items" :key="item.title">
            <p class="font-mono text-2xs tracking-widest uppercase text-brass-500">{{ item.label }}</p>
            <dt class="mt-3 text-base font-medium text-mist-100">{{ item.title }}</dt>
            <dd class="mt-2 text-sm leading-relaxed text-mist-400">{{ item.description }}</dd>
          </div>
        </dl>
      </div>
    </Container>
  </section>
</template>
