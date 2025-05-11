<script setup lang="ts">
import type { Content } from "@prismicio/client";
import { RichTextGlideText, RichTextHeading2 } from "#components";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.BentoSlice>([
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
    <!-- Placeholder component for bento (variation: {{ slice.variation }}) Slices -->
    <PrismicRichText
      :field="slice.primary.heading"
      :components="{ heading2: RichTextHeading2, em: RichTextGlideText }"
    />
    <PrismicRichText :field="slice.primary.body" />
    <template v-for="item in slice.primary.bento" :key="item.title">
      <!-- {{ item }} -->
      <PrismicRichText :field="item.title" />
      <PrismicRichText :field="item.body" />
      <PrismicImage :field="item.image" />
    </template>
  </Bounded>
</template>
