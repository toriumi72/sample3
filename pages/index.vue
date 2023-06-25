<script setup lang="ts">
const items = ref<any>()

const onGetItems = async () => {
  const response = await useFetch('https://qiita.com/api/v2/items')
  items.value = response.data._rawValue
}
</script>

<template>
  <div>
    <div>
      API-test-app
    </div>
    <div>
      <button @click="onGetItems">
        取得する
      </button>
    </div>
    <div v-for="(item, index) in items" :key="index" class="flex">
      <div>
        {{ index + 1 }}
      </div>
      <div>
        <nuxt-link :to="item.url">
          {{ item.title }}
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>


