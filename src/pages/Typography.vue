<template>
  <q-page class="flex column q-pa-md">
    <span class="text-h1">Headline 1</span>
    <span class="text-h2">Headline 2</span>
    <span class="text-h3">Headline 3</span>
    <span class="text-h4">Headline 4</span>
    <span class="text-h5">Headline 5</span>
    <span class="text-h6">Headline 6</span>

    <q-separator />

    <span class="text-subtitle1">Subtitle 1</span>
    <span class="text-subtitle2">Subtitle 2</span>

    <q-separator />

    <p class="text-body1">ubkjbhkjhklj kjhnkjbnkj lnhkln  nkjbhnkjhnkjhnbkjhkjbhnkjbkjhb kjhkjhkjhkjhkjhkj kjhkjhkjhkj jyhv ghfyjgyjg kugkugukgkugkugv tfdtdftyfyugfuig uihuihuik</p>
    <p class="text-body2">ubkjbhkjhklj kjhnkjbnkj lnhkln  nkjbhnkjhnkjhnbkjhkjbhnkjbkjhb kjhkjhkjhkjhkjhkj kjhkjhkjhkj jyhv ghfyjgyjg kugkugukgkugkugv tfdtdftyfyugfuig uihuihuik</p>

    <q-btn
      color="primary"
      :label="isSideMenuOpen ? 'Close side menu' : 'Open side menu'"
      class="q-mt-md"
      @click="toggleSideMenu"
    />
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import useUI from "../composables/useUI"

export default defineComponent({
  name: 'TypographyPage',
  setup() {
    const { toggleSideMenu, isSideMenuOpen } = useUI()

    return {
      isSideMenuOpen,
      toggleSideMenu,
    }
  }
})
</script>
