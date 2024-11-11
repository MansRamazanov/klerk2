<template>
  <div>
    <div class="header">
      <img
        src="../assets/images/klerk.png"
        alt="Логотип Клерк"
        class="header-logo"
      />
      <div class="breadcrumbs">
        <router-link to="/" class="breadcrumb-item">Хлебные крошки</router-link>
        <img src="../assets/images/arrow_right.png" alt="стрелка далее">
        <router-link to="/" class="breadcrumb-item">Хлебные крошки</router-link>
        <img src="../assets/images/arrow_right.png" alt="стрелка далее">
        <router-link to="/" class="breadcrumb-item">Хлебные крошки</router-link>
      </div>
      <h1 class="header-title">Подписки &laquo;Клерка&raquo;</h1>
      <nav class="header-nav">
        <div
          :class="activeNavItem === 1 ? 'nav-item nav-item-active' : 'nav-item'"
          @click="activeNavItem = 1"
        >
          Рассылки
        </div>
        <div
          :class="activeNavItem === 2 ? 'nav-item nav-item-active' : 'nav-item'"
          @click="activeNavItem = 2"
        >
          Соцсети
        </div>
        <div
          :class="activeNavItem === 3 ? 'nav-item nav-item-active' : 'nav-item'"
          @click="activeNavItem = 3"
        >
          Мессенджеры
        </div>
      </nav>
    </div>
    <main class="main-container">
      <div class="form-container">
        <h2 class="form-title">
          Выберите рассылки, которые подходят именно вам
        </h2>
        <form class="form-content">
          <input
            type="email"
            placeholder="Электронная почта"
            class="form-input"
          />
          <button @click="SubmitEvent" class="form-button">Подписаться</button>
        </form>
        <div class="form-switcher-container">
          <Switcher
          size="small"/>
          <div class="switcher-text">Подписаться на все рассылки</div>
        </div>
      </div>
      <div class="card-container">
        <CardItem
          v-for="card in cards"
          :key="card.id"
          :title="card.title"
          :subtitle="card.subtitle"
          :content="card.content"
          :img="card.img"
          :contains="card.contains"
          :totalUsers="card.totalUsers"/>
      </div>
    </main>
    <footer class="footer">
      <img src="../assets/images/didnt_know.png" alt="Лого из символов">
    </footer>
  </div>
</template>
<script setup lang="ts">
import CardItem from "@/components/CardItem.vue";
import { ref } from "vue";
import  cards from "../stores/cardData";
import Switcher from "@/components/UI/Switcher.vue";

const activeNavItem = ref(1);
</script>
<style scoped>
.header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.header-logo {
  width: 75px;
  height: 36px;
}

.breadcrumbs {
  display: flex;
  gap: 8px;
  margin-top: 24px;
  font-size: 13px;
  line-height: 16px;
}

.breadcrumb-item {
  color: #999999;
  text-decoration: none;
  border-bottom: 1px solid #e6edff;
}

.header-title {
  font-size: 56px;
  font-weight: 500;
  line-height: 72px;
  margin-top: 24px;
}

.header-nav {
  display: flex;
  margin-top: 24px;
}

.nav-item {
  font-size: 16px;
  line-height: 24px;
  font-weight: 500;
  padding-bottom: 16px;
  margin-right: 24px;
}

.nav-item:hover {
  cursor: pointer;
  color: #5a8cf1;
  opacity: 0.4;
}

.nav-item:last-child {
  margin-right: 0;
}

.nav-item-active {
  border-bottom: 2px solid #5a8cf1;
  color: #5a8cf1;
}

.nav-item-active:hover {
  opacity: 1;
}

.main-container {
  width: 100%;
  padding: 48px;
  background-color: #f5f5f8;
  border-radius: 15px;
}

.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-title {
  font-size: 24px;
  line-height: 32px;
  font-weight: 500;
  margin-bottom: 24px;
}

.form-content {
  width: 100%;
  display: flex;
  justify-content: center;
  background-color: #fff;
  border-radius: 30px 100px 100px 30px;
}

.form-input {
  width: 100%;
  font-size: 16px;
  line-height: 24px;
  font-weight: 400;
  border: none;
  padding: 16px;
  border-radius: 8px;
}

.form-input:focus-visible {
  outline: none;
}

.form-button {
  font-size: 16px;
  line-height: 24px;
  color: #fff;
  background-color: #316fee;
  border: none;
  border-radius: 100px;
  padding: 0px 32px;
  transition: 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.form-button:hover {
  cursor: pointer;
  opacity: 0.8;
  transition: 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.form-switcher-container {
  width: 100%;
  display: flex;
  align-items: center;
  margin-top: 24px;
}

.switcher-text {
    font-size: 14px;
    line-height: 20px;
    margin-left: 8px;
}

.card-container {
  display: grid;
  grid-template-columns: 50% 50%;
  gap: 24px;
  margin-top: 24px;
}

.footer {
  display: flex;
  justify-content: center;
}

@media screen and (max-width: 600px) {
    
  .card-container {
    grid-template-columns: 100%;  
  }  
}



</style>
