<script setup>
defineProps({
  size: { type: String, default: "base" },
});
</script>

<template>
  <span class="inline-flex items-center gap-2.5">
    <svg
      viewBox="0 0 28 28"
      class="w-7 h-7 shrink-0"
      aria-hidden="true"
      fill="none"
    >
      <rect x="0.6" y="0.6" width="26.8" height="26.8" rx="7.5" class="fill-ink-850 stroke-ink-700" stroke-width="1.2" />
      <path d="M14 5.4 22.6 14 14 22.6 5.4 14 14 5.4Z" class="stroke-brass-400" stroke-width="1.3" stroke-linejoin="round" />
      <path d="M14 10.6 17.4 14 14 17.4 10.6 14 14 10.6Z" class="fill-brass-300" />
    </svg>
    <span
      class="font-medium tracking-tight text-mist-100"
      :class="size === 'lg' ? 'text-xl' : 'text-[1.0625rem]'"
    >
      Ezana <span class="text-brass-400">AI</span>
    </span>
  </span>
</template>
