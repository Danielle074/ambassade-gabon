<template>
  <div class="min-h-screen flex flex-col md:flex-row">
    <!-- 🟦 Formulaire à gauche (fond blanc) -->
    <div class="flex w-full md:w-1/2 items-center justify-center bg-white order-2 md:order-1">
      <div class="p-8 w-full max-w-md">
        <!-- Bouton Retour à l'accueil -->
        <div class="mb-6">
          <button
            @click="goToHome"
            class="inline-flex items-center gap-2 text-[#3A75C4] hover:text-[#009E60] transition-colors"
          >
            <i class='bx bx-arrow-back text-lg'></i>
            <span class="text-sm font-medium">Retour à l'accueil</span>
          </button>
        </div>

        <!-- Logo -->
        <div class="flex flex-col items-center mb-6">
          <img :src="formLogo" alt="Logo Ambassade" class="w-52 h-auto mb-2" />
          <h2 class="text-2xl font-bold text-[#3A75C4]">Bienvenue</h2>
        </div>

        <!-- Formulaire (sans soumission) -->
        <form class="space-y-5">
          <div>
            <input
              type="email"
              placeholder="votre@email.com"
              v-model="email"
              class="w-full px-4 py-2 border border-[#3A75C4] rounded-lg focus:ring-2 focus:ring-[#3A75C4] focus:outline-none"
              required
            />
          </div>

          <div class="relative">
            <input
              :type="showPassword ? 'text' : 'password'"
              placeholder="* * * * * * * *"
              v-model="password"
              class="w-full px-4 py-2 border border-[#3A75C4]/50 rounded-lg focus:ring-2 focus:ring-[#3A75C4] focus:outline-none pr-10"
              required
            />
            <!-- Bouton œil pour voir/masquer le mot de passe -->
            <button
              type="button"
              @click="togglePasswordVisibility"
              class="absolute inset-y-0 right-0 flex items-center pr-3 text-gray-500 hover:text-[#3A75C4]"
            >
              <i :class="showPassword ? 'bx bx-hide' : 'bx bx-show'" class="text-lg"></i>
            </button>
          </div>

          <div class="flex items-center justify-between text-sm text-gray-600">
            <label class="flex items-center space-x-2">
              <input type="checkbox" v-model="rememberMe" class="rounded text-[#3A75C4] focus:ring-[#3A75C4]" />
              <span>Rester connecté</span>
            </label>
            <a href="#" class="text-[#3A75C4] hover:underline">Mot de passe oublié ?</a>
          </div>

          <!-- 🔗 Bouton Se connecter en tant que router-link -->
          <router-link
            to="/dashboard"
            class="w-full bg-[#3A75C4] hover:bg-[#2a5a9e] text-white py-2 rounded-full font-semibold transition duration-200 text-center block"
          >
            Se connecter
          </router-link>
        </form>

        <!-- Créer un compte -->
        <p class="text-center text-gray-600 text-sm mt-4">
          Pas encore de compte ?
          <router-link to="/creer-compte" class="text-[#3A75C4] font-semibold hover:underline">
            Créer un compte
          </router-link>
        </p>

        <p class="text-center text-gray-500 text-sm mt-8 leading-tight">
          Ambassade de la République Gabonaise en Guinée
        </p>
      </div>
    </div>

    <!-- 🖼️ Image à droite -->
    <div class="hidden md:flex md:w-1/2 relative overflow-hidden order-1 md:order-2 bg-[#3A75C4]/20">
      <img
        :src="loginImage"
        alt="Ambassade Gabon"
        class="w-full h-full object-cover opacity-90"
      />

      <!-- Overlay bleu foncé léger -->
      <div class="absolute inset-0 bg-black/20 z-10"></div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import formLogo from "@/assets/images/Gabonarmoirie.png"
import loginImage from "@/assets/images/hero3.jpg"

const router = useRouter()

// Données du formulaire
const email = ref('')
const password = ref('')
const rememberMe = ref(false)
const showPassword = ref(false)

// Fonction pour basculer la visibilité du mot de passe
const togglePasswordVisibility = () => {
  showPassword.value = !showPassword.value
}

// Fonction pour naviguer vers l'accueil
const goToHome = () => {
  router.push('/')
}
</script>

<style scoped>
body {
  font-family: "Poppins", sans-serif;
}

/* Style pour le champ mot de passe avec l'œil */
.relative input[type="password"],
.relative input[type="text"] {
  padding-right: 2.5rem;
}
</style>
