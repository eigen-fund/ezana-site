<script setup>
const title = "Ezana AI — the AI engine for enterprise workflow automation";
const description =
  "Ezana AI deploys an ontology of your business and automates the workflows on top of it, with controls, compliance and an append-only audit trail. Case studies in banking lending and proprietary trading risk.";

useHead({
  htmlAttrs: { lang: "en", class: "dark" },
  title,
  titleTemplate: (chunk) => (chunk && chunk !== title ? `${chunk} — Ezana AI` : title),
  meta: [
    { name: "description", content: description },
    { name: "theme-color", content: "#07080a" },
    { name: "color-scheme", content: "dark" },
    { property: "og:type", content: "website" },
    { property: "og:site_name", content: "Ezana AI" },
    { property: "og:title", content: title },
    { property: "og:description", content: description },
    { name: "twitter:card", content: "summary_large_image" },
    { name: "twitter:title", content: title },
    { name: "twitter:description", content: description },
  ],
  link: [
    { rel: "icon", type: "image/svg+xml", href: "/favicon.svg" },
    { rel: "preconnect", href: "https://fonts.googleapis.com" },
    { rel: "preconnect", href: "https://fonts.gstatic.com", crossorigin: "" },
    {
      rel: "stylesheet",
      href: "https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap",
    },
  ],
  bodyAttrs: {
    class: "font-display antialiased",
  },
});
</script>

<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
