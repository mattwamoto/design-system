<template>
  <div v-if="hasSpecialSponsor" class="mb-8">
    <v-divider class="mx-auto" />

    <div class="d-flex align-center justify-center my-1 px-4">
      <small class="font-weight-bold me-4 text-no-wrap">Special Sponsor</small>

      <sponsor-card
        min-height="64"
        slug="teamwork"
        width="240"
      />
    </div>

    <v-divider class="mx-auto" />
  </div>
</template>

<script setup>
  // Components
  import SponsorCard from '@/components/sponsor/Card.vue'

  // Stores
  import { useSponsorsStore } from '@/store/sponsors'

  // Utilities
  import { computed } from 'vue'

  const store = useSponsorsStore()

  const hasSpecialSponsor = computed(() => store.byTier[-2]?.length > 0)
</script>
