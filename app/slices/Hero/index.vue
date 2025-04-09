<script setup lang="ts">
import type { Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.HeroSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ])
);
</script>

<template>
  <Bounded
    :data-slice-type="slice.slice_type"
    :data-slice-variation="slice.variation"
  >
    <!-- Placeholder component for hero (variation: {{ slice.variation }}) Slices -->

    <!-- {{ slice }} -->

    <div class="text-center relative">
      <PrismicText
        :field="slice.primary.heading"
        class="mx-auto max-w-3xl text-balance text-5xl font-medium"
        wrapper="h1"
      />
      <PrismicText
        :field="slice.primary.body"
        class="mx-auto mt-6 max-w-md text-balance text-gray-300"
        wrapper="p"
      />
      <div class="flex flex-wrap gap-8 justify-center mt-8">
        <PrismicLink
          v-for="cta in slice.primary.ctas"
          :key="cta.key"
          class="buttonLink"
          :field="cta"
        />
      </div>
      <div class="glassContainer mt-16 w-fit">
        <PrismicImage :field="slice.primary.image" class="rounded-lg" />
      </div>
    </div>
    <!-- Text balance wraps the text in a modern way -->
  </Bounded>
</template>
