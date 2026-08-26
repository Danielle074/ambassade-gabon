<template>
  <div class="min-h-screen bg-gray-50">
    <!-- HERO -->
    <section
      class="py-20 bg-cover bg-center"
      :style="{ backgroundImage: `url(${bgHero})` }"
    >
      <div class="max-w-7xl mx-auto px-6 lg:px-8 grid lg:grid-cols-2 gap-16 items-center">

        <!-- TEXTE GAUCHE -->
        <div>
          <!-- Logo -->
          <img
            :src="logoAmbassade"
            class="w-20 mb-6"
            alt="Logo Gabon"
          />

          <!-- Titre -->
          <h1 class="text-4xl lg:text-5xl font-bold text-gray-900 leading-tight mb-6">
            Ambassade de la République Gabonaise
            en République de Guinée
          </h1>

          <!-- Texte -->
          <p class="text-gray-600 mb-8 max-w-xl">
            Ut velit mauris, egestas sed, gravida nec, ornare ut, mi.
            Aenean ut orci vel massa suscipit pulvinar.
            Nulla sollicitudin.
          </p>

          <!-- Boutons -->
          <div class="flex items-center gap-6">
            <router-link
              to="/services"
              class="bg-[#009E60] text-white px-8 py-4 rounded-xl font-semibold shadow-lg hover:bg-[#006640] transition"
            >
              Button 1
            </router-link>

            <a
              href="#"
              class="text-gray-700 font-semibold flex items-center gap-2 hover:text-[#009E60]"
            >
              Voir plus →
            </a>
          </div>
        </div>

        <!-- IMAGES DROITE -->
        <div class="grid grid-cols-2 gap-6">
          <img
            :src="heroPhoto1"
            class="rounded-2xl shadow-lg object-cover h-48 w-full"
          />
          <img
            :src="heroPhoto2"
            class="rounded-2xl shadow-lg object-cover h-64 w-full mt-10"
          />
          <img
            :src="heroPhoto3"
            class="rounded-2xl shadow-lg object-cover h-64 w-full"
          />
          <img
            :src="heroPhoto4"
            class="rounded-2xl shadow-lg object-cover h-48 w-full"
          />
        </div>
      </div>
    </section>

    <!-- Message de bienvenue - 3 photos de même taille -->
    <section class="py-20 bg-white relative overflow-hidden">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold text-[#009E60] mb-4">MOT DE BIENVENUE</h2>
          <div class="w-24 h-1 bg-[#FCD116] mx-auto"></div>
        </div>

        <!-- 3 photos alignées horizontalement de même taille -->
        <div class="flex flex-col lg:flex-row items-stretch justify-center gap-6 lg:gap-8">

          <!-- Ambassadeur (gauche) -->
          <div class="lg:w-1/3 max-w-sm mx-auto lg:mx-0">
            <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300 h-full flex flex-col">
              <div class="h-80 lg:h-[420px] overflow-hidden flex-shrink-0 bg-gray-100">
                <img
                  :src="ambassadeurImage"
                  alt="Ambassadeur"
                  class="w-full h-full object-cover object-[center_20%]"
                />
              </div>
              <div class="p-6 text-center bg-gradient-to-b from-[#009E60] to-[#006640] text-white flex-grow min-h-[130px] flex flex-col justify-center">
                <h4 class="text-lg font-bold mb-1">M. Persis Lionel Essono Ondo</h4>
                <p class="text-[#FCD116] text-sm font-medium">Ambassadeur Extraordinaire et Plénipotentiaire</p>
              </div>
            </div>
          </div>

          <!-- Président (centre - avancé vers l'avant avec shadow léger) -->
          <div class="lg:w-1/3 max-w-sm mx-auto lg:mx-0 relative z-20 transform scale-105 lg:scale-110">
            <!-- Ombre légère derrière le président -->
            <div class="absolute -inset-3 bg-[#009E60]/5 blur-xl rounded-full"></div>
            <div class="absolute -inset-5 bg-[#FCD116]/5 blur-2xl rounded-full"></div>

            <div class="bg-white rounded-2xl overflow-hidden transform hover:-translate-y-2 transition-all duration-300 h-full flex flex-col shadow-custom border-4 border-[#FCD116] relative z-10">
              <div class="h-80 lg:h-[420px] overflow-hidden flex-shrink-0 bg-gray-100">
                <img
                  :src="presidentImage"
                  alt="Président Persis Lionel Essono Ondo "
                  class="w-full h-full object-cover object-[center_20%]"
                />
              </div>
              <div class="p-6 text-center bg-gradient-to-b from-[#FCD116] to-[#e6a800] text-white flex-grow min-h-[130px] flex flex-col justify-center">
                <h3 class="text-lg font-bold mb-1">S.E. Monsieur Persis Lionel Essono Ondo</h3>
                <p class="text-white text-sm font-medium">Président de la République, Chef de l'État</p>
                <p class="text-white/70 text-xs mt-1">République Gabonaise</p>
              </div>
            </div>
          </div>

          <!-- Ministre (droite) -->
          <div class="lg:w-1/3 max-w-sm mx-auto lg:mx-0">
            <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300 h-full flex flex-col">
              <div class="h-80 lg:h-[420px] overflow-hidden flex-shrink-0 bg-gray-100">
                <img
                  :src="ministreImage"
                  alt="Ministre"
                  class="w-full h-full object-cover object-[center_20%]"
                />
              </div>
              <div class="p-6 text-center bg-gradient-to-b from-[#3A75C4] to-[#1e3a6c] text-gray-800 flex-grow min-h-[130px] flex flex-col justify-center">
                <h4 class="text-lg font-bold mb-1">Dr. Marie-Édith Tassyla-Ye-Doumbeneny</h4>
                <p class="text-[#FCD116] text-sm font-medium">Ministre des Affaires Étrangères</p>
              </div>
            </div>
          </div>

        </div>

        <!-- Texte de bienvenue -->
        <div class="mt-16 bg-gray-50 p-8 rounded-2xl shadow-lg border-l-8 border-[#FCD116]">
          <p class="text-lg text-gray-700 leading-relaxed mb-6 italic">
            "Chers compatriotes,<br>
            Chers amis et partenaires de la République Gabonaise,"
          </p>
          <p class="text-gray-700 leading-relaxed mb-6">
            C'est avec un réel plaisir que nous vous ouvrons les portes d'entrée de l'Ambassade du Gabon en Guinée et celles du Gabon toute entière via ce site web.
          </p>
          <p class="text-gray-700 leading-relaxed">
            En effet, la coopération entre la Guinée et la République Gabonaise date des premières années de l'indépendance du Gabon. Mais, c'est en 1979 que les relations diplomatiques proprement dites ont été établies entre les deux pays. Cet élan de coopération connaîtra un second souffle en 1982 avec la signature de l'Accord général de coopération et de développement, suivi de l'ouverture de l'ambassade du Gabon en Guinée en 1980 et celle de la Guinée au Gabon en 1982.
          </p>
        </div>
      </div>
    </section>

    <!-- Section Services -->
    <section class="py-20 bg-gray-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold text-[#009E60] mb-4">NOS SERVICES</h2>
          <div class="w-24 h-1 bg-[#FCD116] mx-auto mb-4"></div>
          <p class="text-gray-600 text-lg max-w-2xl mx-auto">
            Découvrez l'ensemble de nos services consulaires pour vous accompagner dans vos démarches
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <!-- Visa -->
          <div class="bg-white p-8 rounded-2xl shadow-lg hover:shadow-xl transform hover:-translate-y-2 transition-all duration-300 border-b-4 border-[#FCD116]">
            <div class="w-16 h-16 bg-[#009E60]/10 rounded-2xl flex items-center justify-center mb-6">
              <i class='bx bx-edit text-4xl text-[#009E60]'></i>
            </div>
            <h3 class="text-2xl font-bold text-[#009E60] mb-3">Visa</h3>
            <p class="text-gray-600 mb-4">Demande de visa pour la Guinée et informations sur les procédures.</p>
            <router-link to="/services/visa" class="text-[#3A75C4] font-semibold inline-flex items-center gap-2 hover:gap-3 transition-all">
              En savoir plus <i class='bx bx-right-arrow-alt'></i>
            </router-link>
          </div>

          <!-- Carte consulaire -->
          <div class="bg-white p-8 rounded-2xl shadow-lg hover:shadow-xl transform hover:-translate-y-2 transition-all duration-300 border-b-4 border-[#FCD116]">
            <div class="w-16 h-16 bg-[#009E60]/10 rounded-2xl flex items-center justify-center mb-6">
              <i class='bx bx-id-card text-4xl text-[#009E60]'></i>
            </div>
            <h3 class="text-2xl font-bold text-[#009E60] mb-3">Carte consulaire</h3>
            <p class="text-gray-600 mb-4">Inscription et renouvellement de votre carte consulaire.</p>
            <router-link to="/services/inscription" class="text-[#3A75C4] font-semibold inline-flex items-center gap-2 hover:gap-3 transition-all">
              En savoir plus <i class='bx bx-right-arrow-alt'></i>
            </router-link>
          </div>

          <!-- Autres documents -->
          <div class="bg-white p-8 rounded-2xl shadow-lg hover:shadow-xl transform hover:-translate-y-2 transition-all duration-300 border-b-4 border-[#FCD116]">
            <div class="w-16 h-16 bg-[#009E60]/10 rounded-2xl flex items-center justify-center mb-6">
              <i class='bx bx-file text-4xl text-[#009E60]'></i>
            </div>
            <h3 class="text-2xl font-bold text-[#009E60] mb-3">Autres documents</h3>
            <p class="text-gray-600 mb-4">Demande d'actes d'état civil, certificats et autres documents.</p>
            <router-link to="/services/documents" class="text-[#3A75C4] font-semibold inline-flex items-center gap-2 hover:gap-3 transition-all">
              En savoir plus <i class='bx bx-right-arrow-alt'></i>
            </router-link>
          </div>

          <!-- Documents civils -->
          <div class="bg-white p-8 rounded-2xl shadow-lg hover:shadow-xl transform hover:-translate-y-2 transition-all duration-300 border-b-4 border-[#FCD116]">
            <div class="w-16 h-16 bg-[#009E60]/10 rounded-2xl flex items-center justify-center mb-6">
              <i class='bx bx-certification text-4xl text-[#009E60]'></i>
            </div>
            <h3 class="text-2xl font-bold text-[#009E60] mb-3">Documents civils</h3>
            <p class="text-gray-600 mb-4">Légalisation, certification et authentification de documents.</p>
            <router-link to="/services/legalisation" class="text-[#3A75C4] font-semibold inline-flex items-center gap-2 hover:gap-3 transition-all">
              En savoir plus <i class='bx bx-right-arrow-alt'></i>
            </router-link>
          </div>

          <!-- Titre de voyage -->
          <div class="bg-white p-8 rounded-2xl shadow-lg hover:shadow-xl transform hover:-translate-y-2 transition-all duration-300 border-b-4 border-[#FCD116]">
            <div class="w-16 h-16 bg-[#009E60]/10 rounded-2xl flex items-center justify-center mb-6">
              <i class='bx bx-trip text-4xl text-[#009E60]'></i>
            </div>
            <h3 class="text-2xl font-bold text-[#009E60] mb-3">Titre de voyage</h3>
            <p class="text-gray-600 mb-4">Demande et renouvellement de passeport et titres de voyage.</p>
            <router-link to="/services/passeport" class="text-[#3A75C4] font-semibold inline-flex items-center gap-2 hover:gap-3 transition-all">
              En savoir plus <i class='bx bx-right-arrow-alt'></i>
            </router-link>
          </div>

          <!-- Delivery Express -->
          <div class="bg-white p-8 rounded-2xl shadow-lg hover:shadow-xl transform hover:-translate-y-2 transition-all duration-300 border-b-4 border-[#FCD116]">
            <div class="w-16 h-16 bg-[#009E60]/10 rounded-2xl flex items-center justify-center mb-6">
              <i class='bx bx-package text-4xl text-[#009E60]'></i>
            </div>
            <h3 class="text-2xl font-bold text-[#009E60] mb-3">Delivery Express</h3>
            <p class="text-gray-600 mb-4">Service d'envoi et de réception de documents en express.</p>
            <router-link to="/services/express" class="text-[#3A75C4] font-semibold inline-flex items-center gap-2 hover:gap-3 transition-all">
              En savoir plus <i class='bx bx-right-arrow-alt'></i>
            </router-link>
          </div>
        </div>
      </div>
    </section>

    <!-- Section Démarches consulaires et actualités récentes -->
    <section class="py-20 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <!-- Démarches consulaires -->
          <div>
            <h2 class="text-3xl font-bold text-[#009E60] mb-6 flex items-center gap-3">
              <span class="w-2 h-8 bg-[#FCD116] rounded-full"></span>
              Démarches consulaires
            </h2>
            <div class="space-y-4">
              <router-link to="/services/visa" class="block bg-gray-50 p-5 rounded-xl hover:bg-[#009E60] hover:text-white group transition-all">
                <div class="flex items-center justify-between">
                  <span class="font-semibold text-lg">Comment obtenir un visa ?</span>
                  <i class='bx bx-chevron-right text-2xl group-hover:translate-x-2 transition-transform'></i>
                </div>
              </router-link>
              <router-link to="/services/passeport" class="block bg-gray-50 p-5 rounded-xl hover:bg-[#009E60] hover:text-white group transition-all">
                <div class="flex items-center justify-between">
                  <span class="font-semibold text-lg">Renouvellement de passeport</span>
                  <i class='bx bx-chevron-right text-2xl group-hover:translate-x-2 transition-transform'></i>
                </div>
              </router-link>
              <router-link to="/services/legalisation" class="block bg-gray-50 p-5 rounded-xl hover:bg-[#009E60] hover:text-white group transition-all">
                <div class="flex items-center justify-between">
                  <span class="font-semibold text-lg">Légalisation de documents</span>
                  <i class='bx bx-chevron-right text-2xl group-hover:translate-x-2 transition-transform'></i>
                </div>
              </router-link>
              <router-link to="/services/inscription" class="block bg-gray-50 p-5 rounded-xl hover:bg-[#009E60] hover:text-white group transition-all">
                <div class="flex items-center justify-between">
                  <span class="font-semibold text-lg">Inscription consulaire</span>
                  <i class='bx bx-chevron-right text-2xl group-hover:translate-x-2 transition-transform'></i>
                </div>
              </router-link>
            </div>
          </div>

          <!-- Actualités récentes -->
          <div>
            <h2 class="text-3xl font-bold text-[#009E60] mb-6 flex items-center gap-3">
              <span class="w-2 h-8 bg-[#FCD116] rounded-full"></span>
              Actualités récentes
            </h2>
            <div class="space-y-4">
              <div class="bg-gray-50 p-5 rounded-xl hover:shadow-lg transition-all">
                <div class="flex items-start gap-4">
                  <div class="w-16 h-16 bg-[#3A75C4] rounded-xl flex items-center justify-center text-white font-bold">
                    15 MAR
                  </div>
                  <div>
                    <h3 class="font-semibold text-lg mb-1">Réunion diplomatique</h3>
                    <p class="text-gray-600 text-sm">Rencontre avec le ministre guinéen des Affaires Étrangères</p>
                  </div>
                </div>
              </div>
              <div class="bg-gray-50 p-5 rounded-xl hover:shadow-lg transition-all">
                <div class="flex items-start gap-4">
                  <div class="w-16 h-16 bg-[#009E60] rounded-xl flex items-center justify-center text-white font-bold">
                    10 MAR
                  </div>
                  <div>
                    <h3 class="font-semibold text-lg mb-1">Célébration du 8 Mars</h3>
                    <p class="text-gray-600 text-sm">Journée internationale des droits des femmes</p>
                  </div>
                </div>
              </div>
              <div class="bg-gray-50 p-5 rounded-xl hover:shadow-lg transition-all">
                <div class="flex items-start gap-4">
                  <div class="w-16 h-16 bg-[#FCD116] rounded-xl flex items-center justify-center text-[#009E60] font-bold">
                    05 MAR
                  </div>
                  <div>
                    <h3 class="font-semibold text-lg mb-1">Forum économique</h3>
                    <p class="text-gray-600 text-sm">Promotion des investissements au Gabon</p>
                  </div>
                </div>
              </div>
              <div class="bg-gray-50 p-5 rounded-xl hover:shadow-lg transition-all">
                <div class="flex items-start gap-4">
                  <div class="w-16 h-16 bg-[#3A75C4] rounded-xl flex items-center justify-center text-white font-bold">
                    28 FEV
                  </div>
                  <div>
                    <h3 class="font-semibold text-lg mb-1">Journée culturelle</h3>
                    <p class="text-gray-600 text-sm">Célébration de la culture gabonaise en Guinée</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Section Actualités en cartes (4 cards) -->
    <section class="py-20 bg-gray-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold text-[#009E60] mb-4">ACTUALITÉS RÉCENTES</h2>
          <div class="w-24 h-1 bg-[#FCD116] mx-auto mb-4"></div>
          <p class="text-gray-600 text-lg max-w-2xl mx-auto">
            Restez informé des dernières nouvelles de l'ambassade et du Gabon
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <!-- Actualité 1 -->
          <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300">
            <div class="h-48 overflow-hidden relative">
              <div class="absolute top-4 left-4 bg-[#3A75C4] text-white px-3 py-1 rounded-full text-sm font-semibold z-10">
                Diplomatie
              </div>
              <img :src="actualite1" alt="Actualité diplomatique" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500">
            </div>
            <div class="p-6">
              <div class="flex items-center gap-2 text-sm text-gray-500 mb-3">
                <i class='bx bx-calendar'></i>
                <span>15 Mars 2024</span>
              </div>
              <h3 class="font-bold text-lg mb-2 text-[#009E60]">Rencontre diplomatique de haut niveau</h3>
              <p class="text-gray-600 text-sm mb-4">L'ambassadeur reçu par les autorités guinéennes pour renforcer la coopération bilatérale.</p>
              <router-link to="/actualites/1" class="text-[#3A75C4] font-semibold inline-flex items-center gap-1 hover:gap-2 transition-all">
                Lire la suite <i class='bx bx-right-arrow-alt'></i>
              </router-link>
            </div>
          </div>

          <!-- Actualité 2 -->
          <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300">
            <div class="h-48 overflow-hidden relative">
              <div class="absolute top-4 left-4 bg-[#009E60] text-white px-3 py-1 rounded-full text-sm font-semibold z-10">
                Culture
              </div>
              <img :src="actualite2" alt="Célébration culturelle" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500">
            </div>
            <div class="p-6">
              <div class="flex items-center gap-2 text-sm text-gray-500 mb-3">
                <i class='bx bx-calendar'></i>
                <span>10 Mars 2024</span>
              </div>
              <h3 class="font-bold text-lg mb-2 text-[#009E60]">Célébration de la Journée Internationale de la Femme</h3>
              <p class="text-gray-600 text-sm mb-4">Événement spécial à l'ambassade mettant à l'honneur les femmes gabonaises.</p>
              <router-link to="/actualites/2" class="text-[#3A75C4] font-semibold inline-flex items-center gap-1 hover:gap-2 transition-all">
                Lire la suite <i class='bx bx-right-arrow-alt'></i>
              </router-link>
            </div>
          </div>

          <!-- Actualité 3 -->
          <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300">
            <div class="h-48 overflow-hidden relative">
              <div class="absolute top-4 left-4 bg-[#FCD116] text-[#009E60] px-3 py-1 rounded-full text-sm font-semibold z-10">
                Économie
              </div>
              <img :src="actualite3" alt="Forum économique" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500">
            </div>
            <div class="p-6">
              <div class="flex items-center gap-2 text-sm text-gray-500 mb-3">
                <i class='bx bx-calendar'></i>
                <span>5 Mars 2024</span>
              </div>
              <h3 class="font-bold text-lg mb-2 text-[#009E60]">Forum économique Gabon-Guinée</h3>
              <p class="text-gray-600 text-sm mb-4">Promotion des opportunités d'investissement au Gabon devant les investisseurs guinéens.</p>
              <router-link to="/actualites/3" class="text-[#3A75C4] font-semibold inline-flex items-center gap-1 hover:gap-2 transition-all">
                Lire la suite <i class='bx bx-right-arrow-alt'></i>
              </router-link>
            </div>
          </div>

          <!-- Actualité 4 -->
          <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300">
            <div class="h-48 overflow-hidden relative">
              <div class="absolute top-4 left-4 bg-[#3A75C4] text-white px-3 py-1 rounded-full text-sm font-semibold z-10">
                Communauté
              </div>
              <img :src="actualite4" alt="Journée culturelle" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500">
            </div>
            <div class="p-6">
              <div class="flex items-center gap-2 text-sm text-gray-500 mb-3">
                <i class='bx bx-calendar'></i>
                <span>28 Fev 2024</span>
              </div>
              <h3 class="font-bold text-lg mb-2 text-[#009E60]">Journée culturelle gabonaise en Guinée</h3>
              <p class="text-gray-600 text-sm mb-4">Célébration de la richesse culturelle du Gabon avec la communauté gabonaise en Guinée.</p>
              <router-link to="/actualites/4" class="text-[#3A75C4] font-semibold inline-flex items-center gap-1 hover:gap-2 transition-all">
                Lire la suite <i class='bx bx-right-arrow-alt'></i>
              </router-link>
            </div>
          </div>
        </div>

        <div class="text-center mt-12">
          <router-link
            to="/actualites"
            class="inline-flex items-center gap-2 bg-[#009E60] text-white px-8 py-4 rounded-lg font-semibold hover:bg-[#006640] transition-all"
          >
            Voir toutes les actualités
            <i class='bx bx-right-arrow-alt text-xl'></i>
          </router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Import des 4 photos de fond pour le hero
import heroPhoto1 from '@/assets/images/hero1.jpg'
import heroPhoto2 from '@/assets/images/hero2.jpg'
import heroPhoto3 from '@/assets/images/hero3.jpg'
import heroPhoto4 from '@/assets/images/hero4.jpg'
import bgHero from "@/assets/images/bghero.jpeg"

// Import du logo de l'ambassade
import logoAmbassade from '@/assets/images/Gabonarmoirie.png'

// Import des photos du président, ambassadeur et ministre
import presidentImage from '@/assets/images/president.jpeg'
import ambassadeurImage from '@/assets/images/ambassadeurdugabon.jpeg'
import ministreImage from '@/assets/images/ministredesaffairesetrangeres.jpeg'

// Import des images pour les actualités (4 cards)
import actualite1 from '@/assets/images/actualite1.jpg'
import actualite2 from '@/assets/images/actualite2.jpg'
import actualite3 from '@/assets/images/actualite3.jpg'
import actualite4 from '@/assets/images/actualite4.jpg'
</script>

<style scoped>
/* Transition pour les hover */
.transition-all {
  transition: all 0.3s ease;
}

/* Ombre légère pour le président */
.shadow-\[0_15px_40px_-10px_rgba\(0\,158\,96\,0.15\)\] {
  box-shadow: 0 15px 40px -10px rgba(0, 158, 96, 0.15);
}

/* Effet de flou léger pour l'ombre */
.blur-xl {
  filter: blur(24px);
}

.blur-2xl {
  filter: blur(40px);
}
</style>
