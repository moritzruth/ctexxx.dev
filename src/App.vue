<template>
  <NavigationMenu/>
  <div class="bg-white text-black max-w-1200px w-full mx-auto px-6 sm:px-10" style="min-height: calc(100vh - 160px)">
    <router-view/>
  </div>
  <div class="w-full h-20 space-x-10 flex items-center justify-center">
    <router-link
      v-for="item in items"
      :key="item.to"
      class="uppercase tracking-wide text-sm"
      :to="item.to"
    >
      {{ t(item.labelKey) }}
    </router-link>
  </div>
</template>

<style>
  body {
    font-size: 20px;
  }

  ::selection {
    @apply bg-blue-900 bg-opacity-80 text-white;
  }

  .asterisk-list > li {
    &:not(:last-child) {
      margin-bottom: 5px;
    }

    &::before {
      @apply text-blue-900;
      content: "*";
      margin-right: 5px;
    }
  }
</style>

<i18n lang="yaml">
  en:
    footer:
      tac: Terms & Conditions
      legal: Legal Notice

  de:
    footer:
      tac: AGB
      legal: Impressum
</i18n>

<script>
  import { useI18n } from "vue-i18n"
  import NavigationMenu from "./components/NavigationMenu.vue"

  const FOOTER_LINKS = [
    // {
    //   labelKey: "footer.tac",
    //   to: "/terms-and-conditions"
    // },
    {
      labelKey: "footer.legal",
      to: "/legal-notice"
    }
  ]

  export default {
    name: "App",
    components: { NavigationMenu },
    setup() {
      const { t } = useI18n()
      return {
        t,
        items: FOOTER_LINKS
      }
    }
  }
</script>
