<script setup>
const props = defineProps({
  label: String,
  url: String,
  variant: { type: String, default: "primary" },
});
</script>

<template>
  <NuxtLink
    v-if="label && url"
    :href="url"
    class="group inline-flex items-center gap-2 px-5 py-3 text-sm font-medium rounded-md transition duration-200"
    :class="
      variant === 'primary'
        ? 'bg-brass-400 text-ink-950 hover:bg-brass-300'
        : 'text-mist-200 border border-white/12 hover:border-white/28 hover:text-mist-100'
    "
  >
    {{ label }}
    <Glyph
      name="arrow"
      :size="16"
      class="transition-transform duration-200 group-hover:translate-x-0.5"
      :class="variant === 'primary' ? 'opacity-70' : 'opacity-50'"
    />
  </NuxtLink>
</template>
