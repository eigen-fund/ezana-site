<script setup>
import pageData from "@/data/index.json";

const site = pageData;
</script>

<template>
  <div class="min-h-screen bg-ink-950">
    <a
      href="#platform"
      class="sr-only focus:not-sr-only focus:absolute focus:z-50 focus:px-4 focus:py-2 focus:m-3 focus:rounded-md focus:bg-brass-400 focus:text-ink-950"
    >
      Skip to content
    </a>
    <Navbar :items="site.nav.items" :cta="site.nav.cta" />
    <main>
      <slot />
    </main>
    <Footer
      :blurb="site.footer.blurb"
      :columns="site.footer.columns"
      :legal="site.footer.legal"
      :company="site.company"
    />
  </div>
</template>
