<template>
  <promoted-base
    v-if="ad"
    border
    class="v-vuetify"
    density="comfortable"
  >
    <v-list-item
      :prepend-avatar="src"
      :title="ad.title"
      :append-icon="smAndUp ? 'mdi-open-in-new' : undefined"
      style="min-height: inherit; width: 100%"
      v-bind="attrs"
    >
      <template #subtitle>
        <app-markdown
          v-if="description"
          :content="description"
          class="text-caption"
        />
      </template>
    </v-list-item>
  </promoted-base>
</template>

<script setup>
  // Components
  import PromotedBase from './Base.vue'

  // Composables
  import { useDisplay } from 'vuetify'
  import { createAdProps, useAd } from '@/composables/ad'

  const props = defineProps({
    color: String,

    ...createAdProps(),
  })

  const { ad, attrs, src, description } = useAd(props)
  const { smAndUp } = useDisplay()
</script>

<style lang="sass">
  .v-vuetify
    .powered-by
      color: rgba(0, 0, 0, .6)
      font-size: 0.625rem
      font-weight: 400
      letter-spacing: 0.09375rem
      text-transform: uppercase

    &.theme--dark .powered-by
      color: inherit
</style>
