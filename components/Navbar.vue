<script setup>
const props = defineProps({
  items: Array,
  cta: Object,
});

const open = ref(false);
</script>

<template>
  <header
    class="sticky top-0 z-50 border-b border-white/6 bg-ink-950/80 backdrop-blur-xl supports-[backdrop-filter]:bg-ink-950/65"
  >
    <Container>
      <div class="flex items-center justify-between h-16">
        <a href="#top" class="shrink-0" aria-label="Ezana AI — home">
          <Wordmark />
        </a>

        <nav class="hidden md:flex items-center gap-8" aria-label="Primary">
          <a
            v-for="item of items"
            :key="item.url"
            :href="item.url"
            class="text-sm text-mist-400 transition-colors duration-200 hover:text-mist-100"
          >
            {{ item.title }}
          </a>
        </nav>

        <div class="flex items-center gap-2">
          <NuxtLink
            v-if="cta"
            :href="cta.url"
            class="hidden sm:inline-flex items-center px-4 py-2 text-sm rounded-md text-mist-100 border border-white/12 transition duration-200 hover:border-brass-400/60 hover:text-brass-200"
          >
            {{ cta.label }}
          </NuxtLink>
          <button
            type="button"
            class="inline-flex items-center justify-center w-10 h-10 -mr-2 rounded-md text-mist-300 md:hidden hover:text-mist-100"
            :aria-expanded="open"
            aria-controls="mobile-nav"
            @click="open = !open"
          >
            <span class="sr-only">Toggle navigation</span>
            <Glyph :name="open ? 'close' : 'menu'" :size="20" />
          </button>
        </div>
      </div>

      <nav
        v-show="open"
        id="mobile-nav"
        class="pb-6 md:hidden"
        aria-label="Primary, mobile"
      >
        <ul class="flex flex-col border-t border-white/6">
          <li v-for="item of items" :key="item.url">
            <a
              :href="item.url"
              class="block py-3 text-sm border-b border-white/6 text-mist-300 hover:text-mist-100"
              @click="open = false"
            >
              {{ item.title }}
            </a>
          </li>
          <li v-if="cta" class="pt-4">
            <NuxtLink
              :href="cta.url"
              class="inline-flex px-4 py-2.5 text-sm font-medium rounded-md bg-brass-400 text-ink-950"
            >
              {{ cta.label }}
            </NuxtLink>
          </li>
        </ul>
      </nav>
    </Container>
  </header>
</template>
