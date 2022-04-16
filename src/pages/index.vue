<script setup lang="ts">
import { useUserStore } from '~/stores/user'

const user = useUserStore()
const name = $ref(user.savedName)

const router = useRouter()
const go = () => {
  if (name)
    router.push(`/hi/${encodeURIComponent(name)}`)
}

const { t } = useI18n()

const featureList = [
  { name: 'COMPOSITION API', link: 'https://vuejs.org/guide/extras/composition-api-faq.html' },
  { name: 'ANT DESIGN VUE', link: 'https://www.antdv.com/' },
  { name: 'FILE-BASED ROUTED', link: 'https://github.com/hannoeru/vite-plugin-pages' },
  { name: 'LAYOUTS', link: 'https://github.com/JohnCampionJr/vite-plugin-vue-layouts' },
  { name: 'STORE', link: 'https://pinia.vuejs.org/' },
  { name: 'COMPONENTS AUTO-IMPORTING', link: 'https://github.com/antfu/unplugin-vue-components' },
  { name: 'UNOCSS', link: 'https://github.com/unocss/unocss' },
  { name: 'ICONIFY', link: 'https://icones.netlify.app/' },
  { name: 'I18N', link: 'https://github.com/intlify/vue-i18n-next' },
  { name: 'MARKDOWN', link: 'https://github.com/antfu/vite-plugin-md', isEnd: true },
]
</script>

<template>
  <div>
    <div text-4xl m="xa y4" w="160px" flex="~" justify-around>
      <div i-carbon-campsite />
      <div i-carbon-add />
      <div i-simple-icons-antdesign />
    </div>
    <p>
      <a rel="noreferrer" href="https://github.com/su9er/vitesse-antd" target="_blank">
        Vitesse-antd
      </a>
    </p>
    <p>
      <strong>vitesse-antd</strong>
      {{ t('intro.desc') }}
    </p>

    <p mx8 align-center>
      <template v-for="feature in featureList" :key="feature.name">
        <a :href="feature?.link">{{ feature?.name }}</a>
        <template v-if="!feature?.isEnd">
          /
        </template>
      </template>
    </p>

    <div py-4 />

    <a-input
      v-model:value="name"
      :placeholder="t('intro.whats-your-name')"
      :aria-label="t('intro.whats-your-name')"
      type="text"
      autocomplete="false"
      p="x4 y2"
      w="250px"
      text="center gray-700 dark:gray-200"
      bg="transparent"
      border="~ rounded gray-300 dark:gray-700"
      outline="none active:none"
      @keydown.enter="go"
    />

    <label class="hidden" for="input">{{ t('intro.whats-your-name') }}</label>

    <div>
      <a-button
        :disabled="!name"
        m-3
        size="middle"
        type="primary"
        @click="go"
      >
        {{ t('button.go') }}
      </a-button>
    </div>
  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>
