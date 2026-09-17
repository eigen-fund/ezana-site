<script setup>
import pageData from "@/data/index.json";

const page = ref(pageData);

definePageMeta({
  layout: "default",
});
</script>

<template>
  <div>
    <Hero
      :eyebrow="page.hero.eyebrow"
      :title="page.hero.title"
      :title-accent="page.hero.titleAccent"
      :description="page.hero.description"
      :buttons="page.hero.buttons"
      :notes="page.hero.notes"
    />
    <Principles
      :eyebrow="page.principles.eyebrow"
      :title="page.principles.title"
      :items="page.principles.items"
    />
    <Platform
      :eyebrow="page.platform.eyebrow"
      :title="page.platform.title"
      :description="page.platform.description"
      :items="page.platform.items"
    />
    <Pipeline
      :eyebrow="page.pipeline.eyebrow"
      :title="page.pipeline.title"
      :description="page.pipeline.description"
      :steps="page.pipeline.steps"
    />
    <CaseStudies
      :eyebrow="page.caseStudies.eyebrow"
      :title="page.caseStudies.title"
      :description="page.caseStudies.description"
      :items="page.caseStudies.items"
    />
    <Assurance
      :eyebrow="page.assurance.eyebrow"
      :title="page.assurance.title"
      :description="page.assurance.description"
      :columns="page.assurance.columns"
    />
    <Cta
      :eyebrow="page.cta.eyebrow"
      :title="page.cta.title"
      :description="page.cta.description"
      :buttons="page.cta.buttons"
    />
  </div>
</template>
