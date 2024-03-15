<template>
  <div class="client-server">
    <div class="client-server__wrap">
      <button class="client-server__btn" @click="getWaifu">Get Waifu</button>
      <div class="client-server__img">
        <img :src="img" alt="waifu" />
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'

const apiUrl = 'https://api.waifu.im/search'

const img = ref('')

const getWaifu = async () => {
  try {
    const response = await fetch(apiUrl)
    const data = await response.json()
    if (response.ok) {
      img.value = data.images.map((image: any) => {
        return image.url
      })
    } else {
      console.error('Error fetching waifu')
    }
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
