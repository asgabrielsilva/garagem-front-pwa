<script setup>
import LogoTitle from '@/components/templates/LogoTitle.vue';

import { useAuthStore } from '@/stores/auth';

const authStore = useAuthStore();
</script>
<template>
  <div class="logo_and_menu">
    <logo-title class="mb-2" />
    <div class="divider" />
    <div class="menu">
      <router-link to="/">
        <i class="icon mdi mdi-home-outline" /> Home
      </router-link>
      <div v-if="authStore.loggedIn">
    <router-link  to="/logout">
    <i class="icon mdi mdi-account" /> Logout
    </router-link>
      {{ authStore.user.email }}
    </div>
    <router-link v-else to="/login">
    <i class="icon mdi mdi-account" /> Login
    </router-link>
    </div>
    <div class="divider" />
    <div class="menu">
      <router-link to="/acessorios">
        Acessorios
      </router-link>
      <router-link to="/categorias">
         Categorias
      </router-link>
      <router-link to="/cores">
         Cores
      </router-link>
      <router-link to="/marcas">
         Marcas
      </router-link>
      
    </div>
  </div>
  <logo-title />
</template>
<style scoped>
.mb-2 {
  margin-bottom: 1.5rem;
}

.icon {
  font-size: 2rem;
  align-self: center;
}

.divider {
  margin-top: 1rem;
  border-top: 1px solid #eeeeee;
}

.menu {
  padding: 3rem;
}

.menu a {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #000000;
  gap: 1rem;
  font-size: 1.3rem;
  margin-top: 2.2rem;
}
</style>