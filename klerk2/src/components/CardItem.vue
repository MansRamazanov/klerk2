<template>
  <div class="card-item-container">
    <div class="card-header">
      <div>
        <div class="card-subtitle">
          {{ props.subtitle }}
        </div>
        <div class="card-title">{{ props.title }}</div>
      </div>
      <img :src="imgUrl" alt="логотип карточки" class="card-logo"/>
    </div>
    <div class="card-content">{{ props.content }}</div>
    <div v-for="item in props.contains" :key="item.id" class="card-containts">
      <img src="../assets/images/16.png" alt="Зеленая галочка" class="card-containts-logo"/>
      <div class="card-containts-text">{{ item.text }}</div>
    </div>
    <div class="total-users">
        <Switcher size="medium"/>
        <div>Уже получает {{ props.totalUsers }} человек</div>
    </div>
  </div>
</template>
<script setup lang="ts">
import Switcher from './UI/Switcher.vue';

interface Props {
  title: String;
  subtitle: String;
  content: String;
  img: String;
  contains: [string];
  totalUsers: Number;
}

const props = defineProps<Props>();


const imgUrl = new URL(`../assets/images/${props.img}.png`, import.meta.url).href

</script>
<style scoped>

.card-item-container {
    display: flex !important;
    flex-direction: column;
    background-color: #fff;
    border-radius: 16px;
    padding: 24px;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.card-subtitle {
    font-size: 13px;
    line-height: 16px;
    color: #999999;
}

.card-title {
    font-size: 20px;
    line-height: 28px;
    font-weight: 500;
}

.card-content {
    position: relative;
    top: -20px;
    font-size: 14px;
    line-height: 20px;
    color: #666666;
    margin-top: 8px;
    max-width: 320px;
}
.card-containts {
    display: flex;
    gap: 8px;
    margin-bottom: 8px;
    font-size: 14px;
    line-height: 20px;
}

.card-containts-logo {
    width: 16px;
    height: 16px;
}

.total-users {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-top: 8px;
    font-size: 14px;
    line-height: 20px;
}

@media screen and (max-width: 900px) {
    .card-logo {
        width: 40px;
        height: 40px;
    }

    .card-content {
        position: static;
        margin-bottom: 16px;
    }
}
</style>
