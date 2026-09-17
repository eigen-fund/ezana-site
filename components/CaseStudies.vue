<script setup>
defineProps({
  eyebrow: String,
  title: String,
  description: String,
  items: Array,
});
</script>

<template>
  <section id="case-studies" class="py-24 border-t border-white/6 sm:py-32 scroll-mt-16">
    <Container>
      <SectionHeading :eyebrow="eyebrow" :title="title" :description="description" />

      <div class="mt-16 space-y-6">
        <article
          v-for="item of items"
          :key="item.index"
          :id="`case-study-${item.index}`"
          class="overflow-hidden border rounded-xl border-white/8 bg-ink-900/50 scroll-mt-20"
        >
          <!-- masthead -->
          <div class="px-8 py-7 border-b border-white/6 bg-ink-850/50 sm:px-10">
            <div class="flex flex-wrap items-baseline gap-x-4 gap-y-2">
              <span class="font-mono text-2xs tracking-widest uppercase text-brass-400">
                Case study {{ item.index }}
              </span>
              <span class="hidden w-px h-3 sm:block bg-white/12" aria-hidden="true" />
              <span class="font-mono text-2xs tracking-widest uppercase text-mist-500">
                {{ item.sector }}
              </span>
              <span class="hidden w-px h-3 sm:block bg-white/12" aria-hidden="true" />
              <span class="font-mono text-2xs tracking-widest uppercase text-mist-500">
                {{ item.name }}
              </span>
            </div>
            <h3 class="max-w-2xl mt-4 text-2xl font-medium tracking-tight text-balance text-mist-100 sm:text-[1.75rem]">
              {{ item.title }}
            </h3>
            <p class="max-w-2xl mt-3 text-base leading-relaxed text-mist-300">{{ item.summary }}</p>
          </div>

          <div class="grid lg:grid-cols-[20rem_1fr]">
            <!-- context rail -->
            <div class="px-8 py-8 border-b lg:border-b-0 lg:border-r border-white/6 sm:px-10">
              <p class="eyebrow text-mist-500">The situation</p>
              <p class="mt-4 text-sm leading-relaxed text-mist-400">{{ item.context }}</p>

              <p class="mt-8 eyebrow text-mist-500">Built with</p>
              <ul class="flex flex-wrap gap-1.5 mt-4">
                <li
                  v-for="tech of item.stack"
                  :key="tech"
                  class="px-2.5 py-1 font-mono border rounded text-2xs border-white/8 bg-ink-850/70 text-mist-400"
                >
                  {{ tech }}
                </li>
              </ul>
            </div>

            <!-- deployment + outcome -->
            <div class="px-8 py-8 sm:px-10">
              <p class="eyebrow text-brass-400">{{ item.deployedTitle }}</p>
              <ul class="mt-5 space-y-3.5">
                <li v-for="line of item.deployed" :key="line" class="flex gap-3 text-sm leading-relaxed text-mist-300">
                  <span class="mt-2 w-1 h-1 rounded-full bg-brass-500 shrink-0" aria-hidden="true" />
                  <span>{{ line }}</span>
                </li>
              </ul>

              <div class="pt-8 mt-8 border-t border-white/6">
                <p class="eyebrow text-brass-400">{{ item.outcomeTitle }}</p>
                <ul class="grid mt-5 gap-x-8 gap-y-3.5 sm:grid-cols-2">
                  <li v-for="line of item.outcome" :key="line" class="flex gap-3 text-sm leading-relaxed text-mist-300">
                    <Glyph name="check" :size="14" class="mt-1 text-brass-500" />
                    <span>{{ line }}</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </article>
      </div>
    </Container>
  </section>
</template>
