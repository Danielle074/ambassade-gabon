<template>
  <div class="min-h-screen bg-gray-50">
        <!-- HERO SECTION -->
    <section
      class="relative min-h-screen flex items-center pt-24 pb-12 text-white overflow-hidden"
    >
      <!-- PISTE DE SLIDES (glissement horizontal) -->
      <div
        class="absolute inset-0 flex transition-transform duration-1000 ease-in-out"
        :style="{ transform: `translateX(-${activeStep * 100}%)` }"
      >
        <div
          v-for="(slide, index) in slides"
          :key="'bg-' + index"
          class="w-full h-full flex-shrink-0 bg-cover bg-center"
          :style="{ backgroundImage: `url(${slide.image})` }"
        ></div>
      </div>

      <!-- Overlay -->
      <div class="absolute inset-0 bg-gradient-to-r from-black/40 via-black/20 to-black/30"></div>
      <div class="absolute inset-0 bg-black/20"></div>

      <div class="relative max-w-7xl mx-auto px-6 lg:px-8 w-full z-10 grid lg:grid-cols-2 gap-12 lg:gap-8 items-center min-h-[calc(100vh-6rem)]">

        <!-- COLONNE GAUCHE : Logo + Titre + Description + Boutons -->
        <div class="flex flex-col justify-center max-w-lg">
          <img
            :src="logoAmbassade"
            class="w-16 sm:w-20 mb-6 object-contain filter drop-shadow-lg"
            alt="Armoiries Gabon"
          />

          <h1 class="text-2xl sm:text-3xl lg:text-4xl font-extrabold text-[#FCD116] leading-tight mb-4 drop-shadow-md">
            Ambassade de la République du Gabon
            en Guinée
          </h1>

          <p class="text-gray-100 text-xs sm:text-sm mb-8 leading-relaxed drop-shadow-sm font-normal">
            Bienvenue sur le portail officiel de l'Ambassade du Gabon en Guinée. Retrouvez l'ensemble de nos services consulaires, démarches administratives et actualités diplomatiques.
          </p>

          <div class="flex items-center gap-6">
            <router-link
              to="/services"
              class="bg-[#FCD116] text-gray-900 px-7 py-3 rounded-full font-bold shadow-lg hover:bg-yellow-400 transition-all text-xs sm:text-sm"
            >
              Nos Services
            </router-link>

            <a
              href="#bienvenue"
              class="text-white font-semibold flex items-center gap-2 hover:text-[#FCD116] transition-all text-xs sm:text-sm group"
            >
              Voir plus <span class="group-hover:translate-x-1 transition-transform">→</span>
            </a>
          </div>
        </div>

        <!-- COLONNE DROITE : Citation + Auteur + Pagination -->
        <div class="flex flex-col justify-center items-start lg:items-end text-left lg:text-right">
          <div class="max-w-xs sm:max-w-sm lg:max-w-md">
            <div class="text-3xl lg:text-4xl font-serif text-white/90 mb-1 lg:text-left">“</div>

            <!-- Transition slide sur le texte -->
            <transition name="slide-text" mode="out-in">
              <div :key="activeStep">
                <p class="text-sm sm:text-base text-gray-100 leading-relaxed mb-6 font-normal drop-shadow-md text-left">
                  {{ slides[activeStep].quote }}
                </p>
                <h4 class="text-xs font-bold tracking-widest text-white uppercase mb-8 drop-shadow-md text-left">
                  {{ slides[activeStep].author }}
                </h4>
              </div>
            </transition>

            <!-- PAGINATION GROSSE ET VISIBLE 🔥 -->
            <div class="flex items-center gap-3 justify-start">
              <button
                v-for="(step, index) in steps"
                :key="index"
                @click="goToSlide(index)"
                class="relative w-12 h-12 sm:w-14 sm:h-14 rounded-full text-sm sm:text-base font-bold flex items-center justify-center border-2 transition-all duration-300 hover:scale-110 shadow-xl"
                :class="activeStep === index
                  ? 'border-[#FCD116] text-[#FCD116] bg-[#FCD116]/20 scale-110 ring-4 ring-[#FCD116]/30'
                  : 'border-white/70 text-white bg-black/40 hover:border-[#FCD116] hover:text-[#FCD116]'"
              >
                <span>{{ step }}</span>
                <!-- Petit indicateur animé sous le bouton actif -->
                <span
                  v-if="activeStep === index"
                  class="absolute -bottom-2 left-1/2 -translate-x-1/2 w-2 h-2 bg-[#FCD116] rounded-full animate-pulse"
                ></span>
              </button>
            </div>
          </div>
        </div>

      </div>

      <!-- Bouton flottant calendrier -->
      <button class="fixed bottom-6 right-6 z-50 bg-[#001D85] border border-yellow-400/30 text-yellow-400 p-3 rounded-2xl shadow-2xl hover:scale-105 transition-transform flex items-center justify-center">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 002-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
        </svg>
      </button>
    </section>

    <!-- MOT DE BIENVENUE -->
    <section id="bienvenue" class="py-20 bg-white relative overflow-hidden">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold text-[#009E60] mb-4">MOT DE BIENVENUE</h2>
          <div class="w-24 h-1 bg-[#FCD116] mx-auto"></div>
        </div>

        <div class="flex flex-col lg:flex-row items-stretch justify-center gap-6 lg:gap-8">
          <!-- Ambassadeur -->
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

          <!-- Président -->
          <div class="lg:w-1/3 max-w-sm mx-auto lg:mx-0 relative z-20 transform scale-105 lg:scale-110">
            <div class="absolute -inset-3 bg-[#009E60]/5 blur-xl rounded-full"></div>
            <div class="absolute -inset-5 bg-[#FCD116]/5 blur-2xl rounded-full"></div>

            <div class="bg-white rounded-2xl overflow-hidden transform hover:-translate-y-2 transition-all duration-300 h-full flex flex-col border-4 border-[#FCD116] relative z-10">
              <div class="h-80 lg:h-[420px] overflow-hidden flex-shrink-0 bg-gray-100">
                <img
                  :src="presidentImage"
                  alt="S.E. Général Brice Clotaire Oligui Nguema"
                  class="w-full h-full object-cover object-[center_20%]"
                />
              </div>
              <div class="p-6 text-center bg-gradient-to-b from-[#FCD116] to-[#e6a800] text-white flex-grow min-h-[130px] flex flex-col justify-center">
                <h3 class="text-lg font-bold mb-1">S.E. Général Brice Clotaire Oligui Nguema</h3>
                <p class="text-white text-sm font-medium">Président de la Transition, Chef de l'État</p>
                <p class="text-white/70 text-xs mt-1">République Gabonaise</p>
              </div>
            </div>
          </div>

          <!-- Ministre -->
          <div class="lg:w-1/3 max-w-sm mx-auto lg:mx-0">
            <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300 h-full flex flex-col">
              <div class="h-80 lg:h-[420px] overflow-hidden flex-shrink-0 bg-gray-100">
                <img
                  :src="ministreImage"
                  alt="Ministre des Affaires Étrangères"
                  class="w-full h-full object-cover object-[center_20%]"
                />
              </div>
              <div class="p-6 text-center bg-gradient-to-b from-[#3A75C4] to-[#1e3a6c] text-white flex-grow min-h-[130px] flex flex-col justify-center">
                <h4 class="text-lg font-bold mb-1">Dr. Marie-Édith Tassyla-Ye-Doumbeneny</h4>
                <p class="text-[#FCD116] text-sm font-medium">Ministre des Affaires Étrangères</p>
              </div>
            </div>
          </div>
        </div>

        <div class="mt-16 bg-gray-50 p-8 rounded-2xl shadow-lg border-l-8 border-[#FCD116]">
          <p class="text-lg text-gray-700 leading-relaxed mb-6 italic">
            "Chers compatriotes,<br>
            Chers amis et partenaires de la République Gabonaise,"
          </p>
          <p class="text-gray-700 leading-relaxed mb-6">
            C'est avec un réel plaisir que nous vous ouvrons les portes de l'Ambassade du Gabon en Guinée via ce site web.
          </p>
          <p class="text-gray-700 leading-relaxed">
            Les relations fraternelles et diplomatiques entre la République Gabonaise et la République de Guinée témoignent d'une coopération historique durable. Ce portail numérique est dédié à faciliter vos démarches consulaires et à renforcer la proximité avec la communauté gabonaise.
          </p>
        </div>
      </div>
    </section>

    <!-- SECTION SERVICES -->
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
          <div class="bg-white p-8 rounded-2xl shadow-lg hover:shadow-xl transform hover:-translate-y-2 transition-all duration-300 border-b-4 border-[#FCD116]">
            <div class="w-16 h-16 bg-[#009E60]/10 rounded-2xl flex items-center justify-center mb-6">
              <i class='bx bx-edit text-4xl text-[#009E60]'></i>
            </div>
            <h3 class="text-2xl font-bold text-[#009E60] mb-3">Visa</h3>
            <p class="text-gray-600 mb-4">Demande de visa pour le Gabon et informations sur les procédures.</p>
            <router-link to="/services/visa" class="text-[#3A75C4] font-semibold inline-flex items-center gap-2 hover:gap-3 transition-all">
              En savoir plus <i class='bx bx-right-arrow-alt'></i>
            </router-link>
          </div>

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

          <div class="bg-white p-8 rounded-2xl shadow-lg hover:shadow-xl transform hover:-translate-y-2 transition-all duration-300 border-b-4 border-[#FCD116]">
            <div class="w-16 h-16 bg-[#009E60]/10 rounded-2xl flex items-center justify-center mb-6">
              <i class='bx bx-trip text-4xl text-[#009E60]'></i>
            </div>
            <h3 class="text-2xl font-bold text-[#009E60] mb-3">Titre de voyage</h3>
            <p class="text-gray-600 mb-4">Demande et renouvellement de passeport et laissez-passer.</p>
            <router-link to="/services/passeport" class="text-[#3A75C4] font-semibold inline-flex items-center gap-2 hover:gap-3 transition-all">
              En savoir plus <i class='bx bx-right-arrow-alt'></i>
            </router-link>
          </div>

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

    <!-- DÉMARCHES & ACTUALITÉS -->
    <section class="py-20 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
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

          <div>
            <h2 class="text-3xl font-bold text-[#009E60] mb-6 flex items-center gap-3">
              <span class="w-2 h-8 bg-[#FCD116] rounded-full"></span>
              Actualités récentes
            </h2>
            <div class="space-y-4">
              <div class="bg-gray-50 p-5 rounded-xl hover:shadow-lg transition-all">
                <div class="flex items-start gap-4">
                  <div class="w-16 h-16 bg-[#3A75C4] rounded-xl flex items-center justify-center text-white font-bold flex-shrink-0">
                    15 MAR
                  </div>
                  <div>
                    <h3 class="font-semibold text-lg mb-1">Réunion diplomatique</h3>
                    <p class="text-gray-600 text-sm">Rencontre avec les autorités ivoiriennes pour la coopération bilatérale.</p>
                  </div>
                </div>
              </div>
              <div class="bg-gray-50 p-5 rounded-xl hover:shadow-lg transition-all">
                <div class="flex items-start gap-4">
                  <div class="w-16 h-16 bg-[#009E60] rounded-xl flex items-center justify-center text-white font-bold flex-shrink-0">
                    10 MAR
                  </div>
                  <div>
                    <h3 class="font-semibold text-lg mb-1">Célébration du 8 Mars</h3>
                    <p class="text-gray-600 text-sm">Journée internationale des droits des femmes à Abidjan.</p>
                  </div>
                </div>
              </div>
              <div class="bg-gray-50 p-5 rounded-xl hover:shadow-lg transition-all">
                <div class="flex items-start gap-4">
                  <div class="w-16 h-16 bg-[#FCD116] rounded-xl flex items-center justify-center text-[#009E60] font-bold flex-shrink-0">
                    05 MAR
                  </div>
                  <div>
                    <h3 class="font-semibold text-lg mb-1">Forum économique</h3>
                    <p class="text-gray-600 text-sm">Promotion des opportunités d'investissement au Gabon.</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CARDS ACTUALITÉS -->
    <section class="py-20 bg-gray-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold text-[#009E60] mb-4">TOUTE L'ACTUALITÉ</h2>
          <div class="w-24 h-1 bg-[#FCD116] mx-auto mb-4"></div>
          <p class="text-gray-600 text-lg max-w-2xl mx-auto">
            Restez informé des dernières nouvelles de l'ambassade et du Gabon
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300">
            <div class="h-48 overflow-hidden relative">
              <span class="absolute top-4 left-4 bg-[#3A75C4] text-white px-3 py-1 rounded-full text-xs font-semibold z-10">
                Diplomatie
              </span>
              <img :src="actualite1" alt="Actualité diplomatique" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500">
            </div>
            <div class="p-6">
              <div class="flex items-center gap-2 text-sm text-gray-500 mb-3">
                <i class='bx bx-calendar'></i>
                <span>15 Mars 2026</span>
              </div>
              <h3 class="font-bold text-lg mb-2 text-[#009E60]">Rencontre diplomatique</h3>
              <p class="text-gray-600 text-sm mb-4">Renforcement des liens bilatéraux entre le Gabon et la Côte d'Ivoire.</p>
              <router-link to="/actualites/1" class="text-[#3A75C4] font-semibold inline-flex items-center gap-1 hover:gap-2 transition-all">
                Lire la suite <i class='bx bx-right-arrow-alt'></i>
              </router-link>
            </div>
          </div>

          <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300">
            <div class="h-48 overflow-hidden relative">
              <span class="absolute top-4 left-4 bg-[#009E60] text-white px-3 py-1 rounded-full text-xs font-semibold z-10">
                Culture
              </span>
              <img :src="actualite2" alt="Célébration culturelle" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500">
            </div>
            <div class="p-6">
              <div class="flex items-center gap-2 text-sm text-gray-500 mb-3">
                <i class='bx bx-calendar'></i>
                <span>10 Mars 2026</span>
              </div>
              <h3 class="font-bold text-lg mb-2 text-[#009E60]">Journée de la Femme</h3>
              <p class="text-gray-600 text-sm mb-4">Événement mettant à l'honneur les femmes gabonaises de la diaspora.</p>
              <router-link to="/actualites/2" class="text-[#3A75C4] font-semibold inline-flex items-center gap-1 hover:gap-2 transition-all">
                Lire la suite <i class='bx bx-right-arrow-alt'></i>
              </router-link>
            </div>
          </div>

          <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300">
            <div class="h-48 overflow-hidden relative">
              <span class="absolute top-4 left-4 bg-[#FCD116] text-[#009E60] px-3 py-1 rounded-full text-xs font-semibold z-10">
                Économie
              </span>
              <img :src="actualite3" alt="Forum économique" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500">
            </div>
            <div class="p-6">
              <div class="flex items-center gap-2 text-sm text-gray-500 mb-3">
                <i class='bx bx-calendar'></i>
                <span>05 Mars 2026</span>
              </div>
              <h3 class="font-bold text-lg mb-2 text-[#009E60]">Forum d'investissements</h3>
              <p class="text-gray-600 text-sm mb-4">Présentation des opportunités de relance économique au Gabon.</p>
              <router-link to="/actualites/3" class="text-[#3A75C4] font-semibold inline-flex items-center gap-1 hover:gap-2 transition-all">
                Lire la suite <i class='bx bx-right-arrow-alt'></i>
              </router-link>
            </div>
          </div>

          <div class="bg-white rounded-2xl shadow-lg overflow-hidden transform hover:-translate-y-2 transition-all duration-300">
            <div class="h-48 overflow-hidden relative">
              <span class="absolute top-4 left-4 bg-[#3A75C4] text-white px-3 py-1 rounded-full text-xs font-semibold z-10">
                Communauté
              </span>
              <img :src="actualite4" alt="Journée culturelle" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500">
            </div>
            <div class="p-6">
              <div class="flex items-center gap-2 text-sm text-gray-500 mb-3">
                <i class='bx bx-calendar'></i>
                <span>28 Fév 2026</span>
              </div>
              <h3 class="font-bold text-lg mb-2 text-[#009E60]">Rencontre Communautaire</h3>
              <p class="text-gray-600 text-sm mb-4">Échanges chaleureux avec la communauté gabonaise résidant en Côte d'Ivoire.</p>
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
import { ref, onMounted, onUnmounted } from 'vue'

// ⚠️ Vérifiez ces imports : utilisez exactement les images déjà présentes dans votre projet.
import hero1 from "@/assets/images/presidentdugabon.png"
import hero2 from "@/assets/images/president.jpeg"
import hero3 from "@/assets/images/ministredesaffairesetrangeres.jpeg"

import logoAmbassade from '@/assets/images/Gabonarmoirie.png'

// Import des personnalités
import presidentImage from '@/assets/images/president.jpeg'
import ambassadeurImage from '@/assets/images/ambassadeurdugabon.jpeg'
import ministreImage from '@/assets/images/ministredesaffairesetrangeres.jpeg'

// Import des actualités
import actualite1 from '@/assets/images/actualite1.jpg'
import actualite2 from '@/assets/images/actualite2.jpg'
import actualite3 from '@/assets/images/actualite3.jpg'
import actualite4 from '@/assets/images/actualite4.jpg'

// Slide active (0 = slide 1 affichée immédiatement au chargement)
const activeStep = ref(0)

// Tableau des 3 slides : image + texte + auteur
const slides = ref([
  {
    image: hero1,
    quote: "Notre engagement est de renforcer les liens d'amitié et de coopération entre le Gabon et la Guinée, tout en offrant un service consulaire de qualité à nos concitoyens.",
    author: "SEM BRICE CLOTAIRE OLIGUI NGUEMA"
  },
  {
    image: hero2,
    quote: "Texte de la deuxième slide. À personnaliser selon le message que vous souhaitez mettre en avant.",
    author: "AUTEUR 2"
  },
  {
    image: hero3,
    quote: "Texte de la troisième slide. À personnaliser selon le message que vous souhaitez mettre en avant.",
    author: "AUTEUR 3"
  }
])

// Seulement 3 étapes (1, 2 et 3)
const steps = ref(['01', '02', '03'])

// --- DÉFILEMENT AUTOMATIQUE ---
let intervalId = null

const startAutoPlay = () => {
  intervalId = setInterval(() => {
    activeStep.value = (activeStep.value + 1) % slides.value.length
  }, 6000)
}

const stopAutoPlay = () => {
  if (intervalId) {
    clearInterval(intervalId)
    intervalId = null
  }
}

// Clic manuel sur un numéro
const goToSlide = (index) => {
  activeStep.value = index
  stopAutoPlay()
  startAutoPlay()
}

onMounted(() => {
  startAutoPlay()
})

onUnmounted(() => {
  stopAutoPlay()
})
</script>

<style scoped>
.transition-all {
  transition: all 0.3s ease;
}

.blur-xl {
  filter: blur(24px);
}

.blur-2xl {
  filter: blur(40px);
}

/* Transition pour le texte (glisse depuis la droite) */
.slide-text-enter-active,
.slide-text-leave-active {
  transition: all 0.5s ease;
}

.slide-text-enter-from {
  opacity: 0;
  transform: translateX(30px);
}

.slide-text-leave-to {
  opacity: 0;
  transform: translateX(-30px);
}
</style>
