<template>
  <div class="min-h-screen flex flex-col">
    <!-- Navbar en effet Glassmorphism (fond sombre translucide + flou) -->
    <nav class="fixed top-0 left-0 right-0 z-50 bg-black/5 backdrop-blur-md border-b border-white/20 text-white transition-colors duration-300 shadow-lg">
      <div class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-8 py-3">
        <div class="flex items-center justify-between">
          <div class="flex flex-col gap-1">
            <div class="flex items-center gap-4">
              <img :src="logo1" alt="Armoiries du Gabon" class="h-12 w-auto object-contain">
            </div>
          </div>

          <!-- Mobile menu button -->
          <button @click="toggleMobileMenu" class="lg:hidden text-2xl text-white focus:outline-none">
            ☰
          </button>

          <!-- Desktop menu -->
          <div class="hidden lg:flex items-center gap-2 xl:gap-4 text-sm font-medium">
            <router-link to="/" class="nav-item px-3 py-2 rounded-lg hover:bg-[#FCD116] hover:text-[#009E60] transition-all duration-200" active-class="bg-[#FCD116] text-[#009E60] font-bold">Accueil</router-link>

            <!-- Actualités -->
            <div class="relative group">
              <div class="flex items-center">
                <router-link
                  to="/actualite"
                  class="nav-item px-3 py-2 rounded-l-lg hover:bg-[#FCD116] hover:text-[#009E60] transition-all duration-200"
                  active-class="bg-[#FCD116] text-[#009E60] font-bold"
                >
                  Actualités
                </router-link>
                <button
                  @click.stop="toggleDropdown('actualites')"
                  class="nav-item px-2 py-2 rounded-r-lg hover:bg-[#FCD116] hover:text-[#009E60] transition-all duration-200 border-l border-white/20"
                  :class="{ 'bg-[#FCD116] text-[#009E60]': openDropdowns.actualites }"
                >
                  <svg class="w-4 h-4 transition-transform duration-200" :class="{ 'rotate-180': openDropdowns.actualites }" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
                </button>
              </div>
              <!-- Dropdown en Glassmorphism -->
              <div v-show="openDropdowns.actualites" class="absolute top-full left-0 min-w-[220px] bg-black/60 backdrop-blur-md border border-white/10 rounded-xl shadow-2xl z-50 py-2 mt-2">
                <router-link to="/actualites-ambassade" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all border-b border-white/10 last:border-0">
                  Actualités de l'Ambassade
                </router-link>
                <router-link to="/actualites-diplomatique" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all border-b border-white/10 last:border-0">
                  Actualités diplomatiques
                </router-link>
                <router-link to="/actualites-gouvernementale" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all">
                  Actualités gouvernementales
                </router-link>
              </div>
            </div>

            <!-- Ambassade -->
            <div class="relative group">
              <div class="flex items-center">
                <router-link
                  to="/presentation"
                  class="nav-item px-3 py-2 rounded-l-lg hover:bg-[#FCD116] hover:text-[#009E60] transition-all duration-200"
                  active-class="bg-[#FCD116] text-[#009E60] font-bold"
                >
                  Ambassade
                </router-link>
                <button
                  @click.stop="toggleDropdown('ambassade')"
                  class="nav-item px-2 py-2 rounded-r-lg hover:bg-[#FCD116] hover:text-[#009E60] transition-all duration-200 border-l border-white/20"
                  :class="{ 'bg-[#FCD116] text-[#009E60]': openDropdowns.ambassade }"
                >
                  <svg class="w-4 h-4 transition-transform duration-200" :class="{ 'rotate-180': openDropdowns.ambassade }" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
                </button>
              </div>
              <!-- Dropdown en Glassmorphism -->
              <div v-show="openDropdowns.ambassade" class="absolute top-full left-0 min-w-[240px] bg-black/60 backdrop-blur-md border border-white/10 rounded-xl shadow-2xl z-50 py-2 mt-2 max-h-[80vh] overflow-y-auto">
                <router-link to="/presentation" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all border-b border-white/10">Présentation</router-link>
                <router-link to="/ambassadeur" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all border-b border-white/10">L'Ambassadeur</router-link>
                <router-link to="/chancellerie" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all border-b border-white/10">La chancellerie diplomatique</router-link>
                <router-link to="/services-ambassadeur" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all border-b border-white/10">Les Services</router-link>
                <router-link to="/consuls-honoraires" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all border-b border-white/10">Les consuls Honoraires</router-link>
                <router-link to="/calendrier" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all">Calendrier des fêtes légales</router-link>
              </div>
            </div>

            <!-- Services -->
            <div class="relative group">
              <div class="flex items-center">
                <router-link
                  to="/consulat"
                  class="nav-item px-3 py-2 rounded-l-lg hover:bg-[#FCD116] hover:text-[#009E60] transition-all duration-200"
                  active-class="bg-[#FCD116] text-[#009E60] font-bold"
                >
                  Services
                </router-link>
                <button
                  @click.stop="toggleDropdown('services')"
                  class="nav-item px-2 py-2 rounded-r-lg hover:bg-[#FCD116] hover:text-[#009E60] transition-all duration-200 border-l border-white/20"
                  :class="{ 'bg-[#FCD116] text-[#009E60]': openDropdowns.services }"
                >
                  <svg class="w-4 h-4 transition-transform duration-200" :class="{ 'rotate-180': openDropdowns.services }" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
                </button>
              </div>
              <!-- Dropdown en Glassmorphism -->
              <div v-show="openDropdowns.services" class="absolute top-full left-0 min-w-[220px] bg-black/60 backdrop-blur-md border border-white/10 rounded-xl shadow-2xl z-50 py-2 mt-2">
                <router-link to="/consulat" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all border-b border-white/10">Le consulat</router-link>
                <router-link to="/rendez-vous" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all border-b border-white/10">Prise de rendez-vous</router-link>
                <router-link to="/demarche-ligne" class="block px-4 py-2 text-sm text-white/90 hover:bg-[#FCD116] hover:text-[#009E60] transition-all">Vos démarches en ligne</router-link>
              </div>
            </div>

            <!-- Bouton de connexion -->
            <router-link
              to="/connexion"
              class="bg-[#FCD116] text-[#009E60] px-5 py-2 rounded-full font-semibold hover:bg-[#009E60] hover:text-white transition-all ml-4 flex items-center gap-2 shadow-md hover:shadow-lg"
            >
              <i class='bx bx-user text-lg'></i>
              Connexion
            </router-link>
          </div>
        </div>

        <!-- Mobile menu Glassmorphism -->
        <div v-show="isMobileMenuOpen" class="lg:hidden mt-4 pb-4 bg-black/70 backdrop-blur-md border border-white/10 shadow-2xl rounded-2xl p-4">
          <div class="flex flex-col gap-2">
            <router-link to="/" class="block px-3 py-2 rounded hover:bg-[#FCD116] hover:text-[#009E60] text-white">Accueil</router-link>

            <!-- Version mobile -->
            <div v-for="menu in mobileMenus" :key="menu.key">
              <div class="flex items-center justify-between px-3 py-2 rounded hover:bg-[#FCD116] hover:text-[#009E60] text-white">
                <router-link :to="menu.path" class="flex-1">{{ menu.label }}</router-link>
                <button @click.stop="toggleSubmenu(menu.key)" class="p-1">
                  <svg class="w-4 h-4 transition-transform duration-200" :class="{'rotate-90': openSubmenus[menu.key]}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                </button>
              </div>
              <div v-show="openSubmenus[menu.key]" class="ml-4 flex flex-col gap-1 text-sm">
                <router-link v-for="item in menu.items" :key="item.path" :to="item.path" class="block px-3 py-1 hover:bg-[#FCD116] hover:text-[#009E60] text-white/80 rounded">
                  {{ item.label }}
                </router-link>
              </div>
            </div>

            <router-link to="/videos" class="block px-3 py-2 rounded hover:bg-[#FCD116] hover:text-[#009E60] text-white">Vidéos</router-link>
            <router-link to="/connexion" class="block px-3 py-2 rounded bg-[#FCD116] text-[#009E60] font-semibold text-center mt-2">Connexion</router-link>
          </div>
        </div>
      </div>
    </nav>

    <!-- Main content -->
    <main class="flex-1">
      <div class="flex-1">
        <router-view></router-view>
      </div>

      <!-- Footer -->
      <footer class="bg-gradient-to-b from-[#009E60] to-[#006640] text-white relative overflow-hidden -mt-1">
        <!-- Vagues décoratives -->
        <div class="absolute top-0 left-0 right-0 transform -translate-y-1">
          <svg class="w-full h-12 sm:h-16" viewBox="0 0 1200 120" preserveAspectRatio="none">
            <path d="M0,0V46.29c47.79,22.2,103.59,32.17,158,28,70.36-5.37,136.33-33.31,206.8-37.5C438.64,32.43,512.34,53.67,583,72.05c69.27,18,138.3,24.88,209.4,13.08,36.15-6,69.85-17.84,104.45-29.34C989.49,25,1113-14.29,1200,52.47V0Z" opacity=".25" fill="currentColor" class="text-white"></path>
            <path d="M0,0V15.81C13,36.92,27.64,56.86,47.69,72.05,99.41,111.27,165,111,224.58,91.58c31.15-10.15,60.09-26.07,89.67-39.8,40.92-19,84.73-46,130.83-49.67,36.26-2.85,70.9,9.42,98.6,31.56,31.77,25.39,62.32,62,103.63,73,40.44,10.79,81.35-6.69,119.13-24.28s75.16-39,116.92-43.05c59.73-5.85,113.28,22.88,168.9,38.84,30.2,8.66,59,6.17,87.09-7.5,22.43-10.89,48-26.93,60.65-49.24V0Z" opacity=".5" fill="currentColor" class="text-white"></path>
            <path d="M0,0V5.63C149.93,59,314.09,71.32,475.83,42.57c43-7.64,84.23-20.12,127.61-26.46,59-8.63,112.48,12.24,165.56,35.4C827.93,77.22,886,95.24,951.2,90c86.53-7,172.46-45.71,248.8-84.81V0Z" fill="currentColor" class="text-white"></path>
          </svg>
        </div>

        <!-- Contenu du footer -->
        <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-16 sm:pt-20 pb-8 sm:pb-10">
          <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 lg:gap-12 mb-10">
            <!-- Colonne 1 -->
            <div class="sm:col-span-2 lg:col-span-1">
              <div class="flex gap-4 mb-4">
                <img :src="logo1" alt="Armoiries du Gabon" class="h-14 w-auto bg-white/10 p-2 rounded-lg backdrop-blur-sm">
              </div>
              <h3 class="text-[#FCD116] font-semibold text-lg mb-2">Ambassade de la République Gabonaise</h3>
              <p class="text-white/80 text-sm leading-relaxed">
                Représentation diplomatique du Gabon aux Etats-Unis, au service de la communauté gabonaise et du renforcement des relations bilatérales.
              </p>

              <div class="mt-6 flex space-x-3">
                <a href="#" class="p-2 bg-white/10 hover:bg-[#FCD116] hover:text-[#009E60] rounded-full transition-all duration-200">
                  <i class='bx bxl-facebook text-lg'></i>
                </a>
                <a href="#" class="p-2 bg-white/10 hover:bg-[#FCD116] hover:text-[#009E60] rounded-full transition-all duration-200">
                  <i class='bx bxl-twitter text-lg'></i>
                </a>
                <a href="#" class="p-2 bg-white/10 hover:bg-[#FCD116] hover:text-[#009E60] rounded-full transition-all duration-200">
                  <i class='bx bxl-youtube text-lg'></i>
                </a>
                <a href="#" class="p-2 bg-white/10 hover:bg-[#FCD116] hover:text-[#009E60] rounded-full transition-all duration-200">
                  <i class='bx bxl-instagram text-lg'></i>
                </a>
              </div>
            </div>

            <!-- Colonne 2 -->
            <div>
              <h4 class="text-[#FCD116] font-semibold text-lg mb-4 flex items-center gap-2">
                <span class="w-1 h-6 bg-[#3A75C4] rounded-full"></span>
                Ambassade
              </h4>
              <ul class="space-y-3">
                <li>
                  <router-link to="/ambassade/mot" class="text-white/80 hover:text-white transition-all duration-200 flex items-center gap-2 group">
                    <i class='bx bx-chevron-right text-[#FCD116] opacity-0 group-hover:opacity-100 transition-all'></i>
                    <span>Mot de l'ambassadeur</span>
                  </router-link>
                </li>
                <li>
                  <router-link to="/ambassade/equipe" class="text-white/80 hover:text-white transition-all duration-200 flex items-center gap-2 group">
                    <i class='bx bx-chevron-right text-[#FCD116] opacity-0 group-hover:opacity-100 transition-all'></i>
                    <span>Équipe diplomatique</span>
                  </router-link>
                </li>
                <li>
                  <router-link to="/ambassade/coordonnees" class="text-white/80 hover:text-white transition-all duration-200 flex items-center gap-2 group">
                    <i class='bx bx-chevron-right text-[#FCD116] opacity-0 group-hover:opacity-100 transition-all'></i>
                    <span>Coordonnées</span>
                  </router-link>
                </li>
              </ul>
            </div>

            <!-- Colonne 3 -->
            <div>
              <h4 class="text-[#FCD116] font-semibold text-lg mb-4 flex items-center gap-2">
                <span class="w-1 h-6 bg-[#3A75C4] rounded-full"></span>
                Services consulaires
              </h4>
              <ul class="space-y-3">
                <li>
                  <router-link to="/services/visa" class="text-white/80 hover:text-white transition-all duration-200 flex items-center gap-2 group">
                    <i class='bx bx-chevron-right text-[#FCD116] opacity-0 group-hover:opacity-100 transition-all'></i>
                    <span>Visa</span>
                  </router-link>
                </li>
                <li>
                  <router-link to="/services/passeport" class="text-white/80 hover:text-white transition-all duration-200 flex items-center gap-2 group">
                    <i class='bx bx-chevron-right text-[#FCD116] opacity-0 group-hover:opacity-100 transition-all'></i>
                    <span>Passeport</span>
                  </router-link>
                </li>
                <li>
                  <router-link to="/services/legalisation" class="text-white/80 hover:text-white transition-all duration-200 flex items-center gap-2 group">
                    <i class='bx bx-chevron-right text-[#FCD116] opacity-0 group-hover:opacity-100 transition-all'></i>
                    <span>Légalisation</span>
                  </router-link>
                </li>
                <li>
                  <router-link to="/services/inscription" class="text-white/80 hover:text-white transition-all duration-200 flex items-center gap-2 group">
                    <i class='bx bx-chevron-right text-[#FCD116] opacity-0 group-hover:opacity-100 transition-all'></i>
                    <span>Inscription consulaire</span>
                  </router-link>
                </li>
              </ul>
            </div>

            <!-- Colonne 4 -->
            <div>
              <h4 class="text-[#FCD116] font-semibold text-lg mb-4 flex items-center gap-2">
                <span class="w-1 h-6 bg-[#3A75C4] rounded-full"></span>
                Contact
              </h4>
              <div class="space-y-4">
                <div class="flex items-start gap-3">
                  <i class='bx bx-map text-[#FCD116] text-xl mt-1'></i>
                  <p class="text-white/80 text-sm">2112 Leroy Place NW, Washington, DC 20008</p>
                </div>
                <div class="flex items-center gap-3">
                  <i class='bx bx-phone text-[#FCD116] text-xl'></i>
                  <p class="text-white/80">+1 (202) 483 9420</p>
                </div>
                <div class="flex items-center gap-3">
                  <i class='bx bx-envelope text-[#FCD116] text-xl'></i>
                  <p class="text-white/80">info@ambagabon-us.org</p>
                </div>
                <div class="flex items-center gap-3">
                  <i class='bx bx-time text-[#FCD116] text-xl'></i>
                  <p class="text-white/80">Lun-Ven: 9h - 17h</p>
                </div>
              </div>
            </div>
          </div>

          <!-- Liens rapides -->
          <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-4 py-6 border-t border-white/20">
            <router-link to="/actualites" class="text-white/70 hover:text-[#FCD116] text-sm transition-colors flex items-center gap-1">
              <i class='bx bx-chevron-right text-[#FCD116] text-xs'></i>
              Actualités
            </router-link>
            <router-link to="/relations/bilaterales" class="text-white/70 hover:text-[#FCD116] text-sm transition-colors flex items-center gap-1">
              <i class='bx bx-chevron-right text-[#FCD116] text-xs'></i>
              Relations
            </router-link>
            <router-link to="/guinee/histoire" class="text-white/70 hover:text-[#FCD116] text-sm transition-colors flex items-center gap-1">
              <i class='bx bx-chevron-right text-[#FCD116] text-xs'></i>
              Le Gabon
            </router-link>
            <router-link to="/services/visa" class="text-white/70 hover:text-[#FCD116] text-sm transition-colors flex items-center gap-1">
              <i class='bx bx-chevron-right text-[#FCD116] text-xs'></i>
              Services
            </router-link>
            <router-link to="/videos" class="text-white/70 hover:text-[#FCD116] text-sm transition-colors flex items-center gap-1">
              <i class='bx bx-chevron-right text-[#FCD116] text-xs'></i>
              Vidéos
            </router-link>
          </div>

          <!-- Copyright -->
          <div class="mt-6 pt-6 border-t border-white/20">
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center text-white/70 text-xs sm:text-sm gap-4">
              <div>
                <p>© 2024 Ambassade de la République Gabonaise. Tous droits réservés.</p>
                <p class="mt-1 text-xs">près les Etats-Unis d'Amérique - Washington DC</p>
              </div>
              <div class="flex items-center gap-2">
                <span class="hidden sm:inline">Créé par</span>
                <span class="font-bold text-[#FCD116] whitespace-nowrap">SCB SYSTEMS Africa</span>
              </div>
              <div class="flex flex-col sm:flex-row gap-2 sm:gap-4">
                <router-link to="/mentions-legales" class="hover:text-[#FCD116] transition-colors duration-200">
                  Mentions légales
                </router-link>
                <router-link to="/confidentialite" class="hover:text-[#FCD116] transition-colors duration-200">
                  Confidentialité
                </router-link>
              </div>
            </div>
          </div>
        </div>
      </footer>
    </main>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import logo1 from '@/assets/images/Gabonarmoirie.png'

const isMobileMenuOpen = ref(false)

const openDropdowns = reactive({
  actualites: false,
  ambassade: false,
  relations: false,
  services: false,
  guinee: false,
  venir: false
})

const openSubmenus = reactive({
  actualites: false,
  ambassade: false,
  relations: false,
  services: false,
  guinee: false,
  venir: false
})

const mobileMenus = ref([
  {
    key: 'actualites',
    label: 'Actualités',
    path: '/actualite',
    items: [
      { label: 'Actualités de l\'Ambassade', path: '/actualites-ambassade' },
      { label: 'Actualités diplomatiques', path: '/actualites-diplomatique' },
      { label: 'Actualités gouvernementales', path: '/actualites-gouvernementale' }
    ]
  },
  {
    key: 'ambassade',
    label: 'Ambassade',
    path: '/presentation',
    items: [
      { label: 'Présentation', path: '/presentation' },
      { label: 'L\'Ambassadeur', path: '/ambassadeur' },
      { label: 'La chancellerie diplomatique', path: '/chancellerie' },
      { label: 'Les Services', path: '/services-ambassadeur' },
      { label: 'Les consuls Honoraires', path: '/consuls-honoraires' },
      { label: 'Calendrier des fêtes légales', path: '/calendrier' }
    ]
  },
  {
    key: 'services',
    label: 'Services',
    path: '/consulat',
    items: [
      { label: 'Le consulat', path: '/consulat' },
      { label: 'Prise de rendez-vous', path: '/rendez-vous' },
      { label: 'Vos démarches en ligne', path: '/construction' }
    ]
  },
  {
    key: 'guinee',
    label: 'Le Gabon',
    path: '/construction',
    items: [
      { label: 'Présentation du Gabon', path: '/construction' },
      { label: 'Le Président de la République', path: '/construction' },
      { label: 'Le Gouvernement', path: '/construction' },
      { label: 'Les institutions de l\'Etat', path: '/construction' },
      { label: 'Les anciens Ambassadeurs', path: '/construction' }
    ]
  },
  {
    key: 'venir',
    label: 'Venir',
    path: '/construction',
    items: [
      { label: 'Visas', path: '/construction' },
      { label: 'Visiter le Gabon', path: '/construction' },
      { label: 'Investir au Gabon', path: '/construction' }
    ]
  }
])

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const toggleDropdown = (menu) => {
  openDropdowns[menu] = !openDropdowns[menu]
}

const toggleSubmenu = (key) => {
  openSubmenus[key] = !openSubmenus[key]
}
</script>

<style scoped>
.nav-item {
  transition: all 0.3s ease;
}

.rotate-180 {
  transform: rotate(180deg);
}

.rotate-90 {
  transform: rotate(90deg);
}

.transition-transform {
  transition-property: transform;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 200ms;
}
</style>
