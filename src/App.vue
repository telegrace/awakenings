<script setup lang="ts">
import { resolveComponent, ref } from 'vue'
import PageLayout from './components/PageLayout.vue'

const LandingPage = resolveComponent('LandingPage')
const CardSelectionPage = resolveComponent('CardSelectionPage')
const ResultsPage = resolveComponent('ResultsPage')

const pages = {
  LandingPage: {
    component: LandingPage,
    subtitle:
      'The ultimate card game designed to enhance conversation and ignite creativity in group sessions.'
  },
  CardSelectionPage: {
    component: CardSelectionPage,
    subtitle: 'Choose a card to reflect your current mood.'
  },
  ResultsPage: {
    component: ResultsPage,
    subtitle: 'Generate a mood inspired by our community.'
  }
}

const currentPage = ref(0)

const handleNextClick = () => {
  console.log('handleNextClick')
  currentPage.value++
}

const handleCardClick = () => {
  console.log('handleCardClick')
  currentPage.value++
}

const handleBackClick = () => {
  currentPage.value--
}

const handleDownloadClick = () => {
  currentPage.value = 1
}
</script>

<template>
  <!-- <PageLayout>
    <h1>grace</h1>
    <template #content>
      <component
        :is="pages[0].component"
        :subtitle="pages[0].subtitle"
        @next-step="currentPage++"
      />
    </template>
  </PageLayout> -->
  <PageLayout>
    <template #content>
      <section v-if="currentPage === 0">
        <header>
          <h1>Awakenings: craft stories, build bonds</h1>
          <h2>
            The ultimate card game designed to enhance conversation and ignite creativity in group
            sessions.
          </h2>
        </header>
        <main>
          <figure>
            <!-- <img src="./assets/logo.png" alt="Awakenings logo" /> -->
            <div class="card"></div>
          </figure>
          <p>
            Choose a visual that reflects your current mood and generate sounds inspired by our
            vibrant community.
          </p>
          <p>
            Combine these elements to weave captivating stories, share experiences, and unleash your
            inner strategist.
          </p>
          <div class="btn-container">
            <button @click="handleNextClick">NEXT</button>
          </div>
        </main>
      </section>
      <section v-if="currentPage === 1">
        <header>
          <h1>Awakenings: craft stories, build bonds</h1>
          <h2>Choose a card to reflect your current mood.</h2>
        </header>
        <main>
          <div class="card-container">
            <div class="row">
              <div @click="handleCardClick" class="card"></div>
              <div @click="handleCardClick" class="card"></div>
              <div @click="handleCardClick" class="card"></div>
            </div>
            <div class="row">
              <div @click="handleCardClick" class="card"></div>
              <div @click="handleCardClick" class="card"></div>
              <div @click="handleCardClick" class="card"></div>
            </div>
            <div class="row">
              <div @click="handleCardClick" class="card"></div>
              <div @click="handleCardClick" class="card"></div>
              <div @click="handleCardClick" class="card"></div>
            </div>
          </div>
        </main>
      </section>
      <section v-if="currentPage === 2">
        <header>
          <h1>Awakenings: craft stories, build bonds</h1>
          <h2>placeholder Does this card reflect your mood?</h2>
        </header>
        <main>
          <figure>
            <!-- <img src="./assets/logo.png" alt="Awakenings logo" /> -->
            <div class="generate-card"></div>
          </figure>

          <div class="btn-container">
            <button @click="handleBackClick">CHANGE CARD</button>
            <button @click="handleDownloadClick">DOWNLOAD YOUR STORY</button>
          </div>
        </main>
      </section>
    </template>
  </PageLayout>
</template>
