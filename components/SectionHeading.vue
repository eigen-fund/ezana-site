<script setup>
defineProps({
  eyebrow: String,
  title: String,
  description: String,
  align: { type: String, default: "left" },
});
</script>

<template>
  <div :class="align === 'center' ? 'max-w-3xl mx-auto text-center' : 'max-w-3xl'">
    <p v-if="eyebrow" class="flex items-center gap-2.5 eyebrow text-brass-400" :class="align === 'center' && 'justify-center'">
      <span class="w-1 h-1 rounded-full bg-brass-400" />
      {{ eyebrow }}
    </p>
    <h2
      v-if="title"
      class="mt-5 text-3xl font-medium tracking-tight text-balance text-mist-100 sm:text-4xl"
    >
      {{ title }}
    </h2>
    <p v-if="description" class="mt-5 text-base leading-relaxed text-mist-400 sm:text-lg">
      {{ description }}
    </p>
  </div>
</template>
