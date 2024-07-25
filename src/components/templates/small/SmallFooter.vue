<script setup>
import { ref } from 'vue';
import { onBeforeRouteUpdate } from 'vue-router';
import { useAuthStore } from '@/stores/auth';

const authStore = useAuthStore();

const showMenu = ref(false);
const confirmLogout = ref(false);

onBeforeRouteUpdate(() => {
  showMenu.value = false;
});
onBeforeRouteUpdate(() => {
  confirmLogout.value = false;
});

</script>
<template>
<div id="logoutConfirm" :style="{ display: confirmLogout ? 'block' : 'none' }">
    <div class="btn" @click="confirmLogout = !confirmLogout">
      Tem certeza?
    </div>
    <router-link to="/logout">
        Sim
    </router-link>
    
  </div>

  <div id="footerMenu" :style="{ display: showMenu ? 'block' : 'none' }">
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
  <div class="icons">
    <RouterLink to="/">
      <i class="mdi mdi-home-outline" />
      Home
    </RouterLink>
    <div v-if="authStore.loggedIn">
    <div class="hamburger" @click="confirmLogout = !confirmLogout">
      <i class="icon mdi mdi-account" /> Logout
    </div>
    </div>
    <router-link v-else to="/login">
    <i class="icon mdi mdi-account" /> Login
    </router-link>
    <div class="hamburger" @click="showMenu = !showMenu">
      <i class="mdi mdi-menu" />
      Menu
    </div>
  </div>
</template>
<style scoped>
#footerMenu {
    position: fixed;
    bottom: 15%;
    right: 0;

    width: 30%;
    border-top: #EEEEEE 1px solid;
    background-color: white;

    display: block;
    padding: 1rem;
}

#footerMenu a {
    display: flex;
    width: 100%;
    justify-content: space-between;
    text-decoration: none;
    color: #282828;
    font-size: 1rem;
    transition: color 0.3s;
}
#logoutConfirm {
    position: fixed;
    bottom: 13%;
    right: 30%;

    width: 40%;
    border-top: #EEEEEE 1px solid;
    background-color: white;

    display: block;
    padding: 1rem;

   
}

#logoutConfirm a {
    display: flex;
    flex-direction: column;
    width: 100%;
    justify-content: space-between;
    text-decoration: none;
    color: #282828;
    font-size: 1rem;
    transition: color 0.3s;
    padding-top: 8px;
}


.icons {
    display: flex;
    width: 100%;
    align-items: center;
    justify-content: space-between;
}

.icons a,
.icons .hamburger {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-decoration: none;
    color: #282828;
    font-size: 1rem;
    transition: color 0.3s;
}

.hamburger:hover {
    cursor: pointer;
}

.btn{
  font-size: 1.1rem;
  color: #282828;
}
</style>