<template>
  <div class="client-server">
    <div class="client-server__wrap">
      <button class="client-server__btn" @click="getWaifu">Get Waifu</button>
      <div class="client-server__img">
        <img :src="img" alt="тут будет твоя waifu" />
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
import { getData } from '@/components/clientServerApp/api'

const apiUrl = 'https://api.waifu.im/search'

const img = ref('')

const getWaifu = async () => {
  try {
    const data = await getData(apiUrl)
    img.value = data.images.map((image: any) => {
      return image.url
    })
  } catch (error) {
    console.error(error)
  }
}
</script>

<style lang="scss">
.client-server {
  &_wrap {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }

  &__img {
    display: flex;
    justify-content: center;
    margin-top: 2rem;
  }

  img {
    width: 100%;
    height: 550px;
    border-radius: 20px;
  }

  &__btn {
    display: block;
    margin: 0 auto;
    padding: 1rem 2rem;
    font-size: 1.5rem;
    border-radius: 10px;
    background-color: var(--color-white);
    color: greenyellow;
    cursor: pointer;
  }
}
</style>
