<script setup>
// Inline, stroke-matched icons. Kept local so the page ships with no icon
// fetch at runtime and every glyph shares one weight.
const props = defineProps({
  name: { type: String, required: true },
  size: { type: [String, Number], default: 20 },
});

const glyphs = {
  graph: [
    ["circle", { cx: 6, cy: 6.5, r: 2.2 }],
    ["circle", { cx: 18, cy: 6.5, r: 2.2 }],
    ["circle", { cx: 12, cy: 18, r: 2.2 }],
    ["path", { d: "M8.2 6.5h7.6" }],
    ["path", { d: "M6.9 8.6l4 7.3" }],
    ["path", { d: "M17.1 8.6l-4 7.3" }],
  ],
  key: [
    ["circle", { cx: 8.5, cy: 8.5, r: 3.6 }],
    ["path", { d: "M11.1 11.1 20 20" }],
    ["path", { d: "M14.6 14.6l-1.9 1.9" }],
    ["path", { d: "M17.3 17.3l-1.9 1.9" }],
  ],
  shield: [
    ["path", { d: "M12 3l7.5 3v5.6c0 4.4-3 7.8-7.5 9.4-4.5-1.6-7.5-5-7.5-9.4V6L12 3z" }],
    ["path", { d: "M9 11.8l2.3 2.3L15.6 9.8" }],
  ],
  pulse: [
    ["path", { d: "M3 13h3.4l2.1-5.4 3 11 2.6-7.2 1.7 2.4h5.2" }],
  ],
  layers: [
    ["path", { d: "M12 3 3 7.4l9 4.4 9-4.4L12 3z" }],
    ["path", { d: "M3 12.2l9 4.4 9-4.4" }],
    ["path", { d: "M3 16.8l9 4.4 9-4.4" }],
  ],
  server: [
    ["rect", { x: 3.5, y: 4, width: 17, height: 6.4, rx: 1.6 }],
    ["rect", { x: 3.5, y: 13.6, width: 17, height: 6.4, rx: 1.6 }],
    ["path", { d: "M7 7.2h.01" }],
    ["path", { d: "M7 16.8h.01" }],
    ["path", { d: "M11 7.2h5" }],
    ["path", { d: "M11 16.8h5" }],
  ],
  arrow: [["path", { d: "M4 12h13.5" }], ["path", { d: "M12.5 7l5 5-5 5" }]],
  check: [["path", { d: "M4.5 12.5l4.5 4.5L19.5 6.5" }]],
  menu: [["path", { d: "M4 7h16" }], ["path", { d: "M4 12h16" }], ["path", { d: "M4 17h16" }]],
  close: [["path", { d: "M6 6l12 12" }], ["path", { d: "M18 6L6 18" }]],
};

const parts = computed(() => glyphs[props.name] ?? []);
</script>

<template>
  <svg
    :width="size"
    :height="size"
    viewBox="0 0 24 24"
    fill="none"
    stroke="currentColor"
    stroke-width="1.35"
    stroke-linecap="round"
    stroke-linejoin="round"
    aria-hidden="true"
    class="shrink-0"
  >
    <component v-for="([tag, attrs], i) of parts" :key="i" :is="tag" v-bind="attrs" />
  </svg>
</template>
