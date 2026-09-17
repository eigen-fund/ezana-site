<script setup>
const props = defineProps({
  eyebrow: String,
  title: String,
  titleAccent: String,
  description: String,
  buttons: Array,
  notes: Array,
});

// Split the headline so one phrase can carry the accent colour.
const titleParts = computed(() => {
  if (!props.title || !props.titleAccent) return { lead: props.title, accent: "", tail: "" };
  const at = props.title.indexOf(props.titleAccent);
  if (at === -1) return { lead: props.title, accent: "", tail: "" };
  return {
    lead: props.title.slice(0, at),
    accent: props.titleAccent,
    tail: props.title.slice(at + props.titleAccent.length),
  };
});
</script>

<template>
  <section id="top" class="relative overflow-hidden isolate">
    <div class="absolute inset-0 -z-10 grid-field opacity-70" aria-hidden="true" />
    <div
      class="absolute inset-0 -z-10"
      style="background: radial-gradient(70% 55% at 50% 0%, rgba(211,173,98,0.15), transparent 70%), linear-gradient(to bottom, transparent 55%, #07080a 100%)"
      aria-hidden="true"
    />

    <Container>
      <div class="grid items-center gap-16 py-20 sm:py-28 lg:grid-cols-[1.05fr_1fr] lg:gap-14 lg:py-32">
        <div>
          <p v-if="eyebrow" class="inline-flex items-center gap-2.5 px-3 py-1.5 border rounded-full border-white/10 bg-ink-900/60 eyebrow text-mist-300">
            <span class="w-1.5 h-1.5 rounded-full bg-brass-400" />
            {{ eyebrow }}
          </p>

          <h1
            v-if="title"
            class="mt-7 text-4xl font-medium leading-[1.08] tracking-tight text-balance text-mist-100 sm:text-5xl lg:text-[3.4rem]"
          >
            {{ titleParts.lead }}<span v-if="titleParts.accent" class="text-brass-300">{{ titleParts.accent }}</span>{{ titleParts.tail }}
          </h1>

          <p v-if="description" class="max-w-xl mt-7 text-base leading-relaxed text-mist-400 sm:text-lg">
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

          <ul v-if="notes?.length" class="flex flex-wrap mt-10 gap-x-6 gap-y-2">
            <li
              v-for="note of notes"
              :key="note"
              class="flex items-center gap-2 font-mono text-2xs tracking-wide uppercase text-mist-500"
            >
              <Glyph name="check" :size="13" class="text-brass-500" />
              {{ note }}
            </li>
          </ul>
        </div>

        <div class="lg:pl-4">
          <TracePanel />
        </div>
      </div>
    </Container>
  </section>
</template>
